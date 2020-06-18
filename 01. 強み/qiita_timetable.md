ラジオ番組をテーマにしたポートフォリオを作成しました。

しかし、週間番組表をサクッと作れるコンポーネントもスニペットも見当たりませんでした。

唯一発見したのが、こちら。(pythonで作成)

このブログを元に、Railsで週間番組表を作成しました。



## スペック

rails 5.2
materialize
slim

## 作り方

1.週間番組表のデータ全てを取得
2.曜日毎に変数に格納
3.曜日毎のカラムに縦に表示させる
4.番組時間１分＝1pxとすることで時間帯を表現

1.週間番組表のデータ全てを取得
https://ststarfield.blog.fc2.com/blog-entry-150.html
radikoの番組表xlmの取得APIのメモ
ラジオをテーマにしたポートフォリオだったため、ここからxmlファイルを落とし、
nokogiriでパースしcsvに変換、spleadsheetでケバ取りをし、1週間分の番組情報をsheedに登録しました。
記事の本筋とはズレるので詳細は割愛します。
よりスマートな方法があるはずですが。

ちなみにラジオ番組のデータはこちらから取得しました。
xmlをnokogiriでパースし各要素を取得し
一度CSVにしてからsheedに登録しているのは、画像urlの最初にドットがあると登録されない、などのエラーがあったため
画像を先にassetに落としておいて、csvに記載されたurlを登録という面倒なことになってます。
スマートな方法をご存知の方、ご教授願います。



2.曜日毎に変数に格納
controller

~~~
  def tbs　＃放送局毎に存在します
    station = 'TBSラジオ'
    start_time = Time.zone.local(2020, 2, 3, 5, 0o0, 0o0)　#番組表は基本的に05:00~なので
    set_timetable(station, start_time)
  end

  def set_timetable(station, start_time)
    day = 24 * 60 * 60　# APIから取得できたのはx分だったため
    # 曜日毎の配列に番組をセット。 order(id: 'ASC')は放送時間順にIDがふられていた為。
    @radios_day1 = Radio.where(station: station).where(start_time: start_time...start_time + day).order(id: 'ASC')
    @radios_day2 = Radio.where(station: station).where(start_time: start_time + day...start_time + day * 2).order(id: 'ASC')
    @radios_day3 = Radio.where(station: station).where(start_time: start_time + day * 2...start_time + day * 3).order(id: 'ASC')
    @radios_day4 = Radio.where(station: station).where(start_time: start_time + day * 3...start_time + day * 4).order(id: 'ASC')
    @radios_day5 = Radio.where(station: station).where(start_time: start_time + day * 4...start_time + day * 5).order(id: 'ASC')
    @radios_day6 = Radio.where(station: station).where(start_time: start_time + day * 5...start_time + day * 6).order(id: 'ASC')
    @radios_day7 = Radio.where(station: station).where(start_time: start_time + day * 6...start_time + day * 7).order(id: 'ASC')
  end
~~~

~~~
#参考までに

create_table "radios", force: :cascade do |t|
    t.string "title", null: false
    t.string "personality"
    t.string "image"
    t.string "station", null: false
    t.datetime "start_time", null: false
    t.datetime "end_time"
    t.integer "length", null: false
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end
~~~

~~~
#参考までに
XML CSV Sheed

CSV.foreach('db/xml/TBSweekly加工済.csv', headers: true) do |row|
  row['filename'] = 'tbslogo.jpg' if row['filename'] == '3cd30990-b9f5-4080-84fa-cc215e99aa94.jpeg'
  Radio.create(
    title: row['title'],
    personality: row['pfm'],
    station: row['station'],
    start_time: row['ft'],
    end_time: row['title'],
    length: row['dur'],
    image: "TBS/#{row['filename']}"
  )
end
~~~

~~~
require 'nokogiri'
require 'csv'
require 'open-uri'

CSV.open('FMTweekly2.csv', 'w') do |csv|
  f = File.open('FMTweekly2.xml')
  doc = Nokogiri::XML(f)
  f.close
  csv << %w[title pfm ft to dur image] # csvへの書き込み

  item_nodes = doc.xpath('//progs/prog')
  item_nodes.each do |item|
    title = item.xpath('title').text
    pfm = item.xpath('pfm').text
    ft = item.xpath('@ft').text
    to = item.xpath('@to').text
    dur = item.xpath('@dur').text
    image = item.xpath('img').text

    csv << [title, pfm, ft, to, dur, image] # csvへの書き込み
    p image
  end
end
~~~




ちなみに
https://tercel-tech.hatenablog.com/entry/2019/07/06/190452
こちらも参考になるかと思います。


https://torina.top/detail/384/