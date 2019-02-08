[GET방식]
```Swift
// 1. 
let url = "http://swiftapi.rubypaper.co.kr:2029/hoppin/movies?version=1&page=\(self.page)&count=30&genreId=&order=releasedateasc"
// 2. 
let apiURI: URL! = URL(string: url)
// 3.
let apidata = try! Data(contentsOf: apiURI)
```
1. 요청하고자 하는 API주소를 url이라는 변수에 저장.
2. 네트워크 주소를 URL객체로 생성, 문자열 형태의 네트워크 주소를 인자값으로 받아 파운데이션 프레임워크에서 사용하는 형식의 주소 객체로 생성.
3. URL 객체를 통해 네트워크 통신을 하고 응답받은 데이터를 Data 객체화 하여 apiData 상수에 저장.

```Swift
// 1.
let apiDictionary = try JSONSerialization.jsonObject(with: apidata, options: []) as! NSDictionary
// 2.       
let hoppin = apiDictionary["hoppin"] as! NSDictionary
let movies = hoppin["movies"] as! NSDictionary
let movie = movies["movie"] as! NSArray
// 3.       
for row in movie {
  let r = row as! NSDictionary
                
  let mvo = MovieVO()
                
  mvo.title = r["title"] as? String
  mvo.description = r["genreNames"] as? String
  mvo.thumnail = r["thumbnailImage"] as? String
  mvo.detail = r["linkUrl"] as? String
  mvo.rating = ((r["ratingAverage"] as! NSString).doubleValue)
                
  self.list.append(mvo)
                
  self.tableView.reloadData()
}
```
1. apiData에 응답받은 데이터를 JSONObject화 하여 사용. NSDictionary타입은 key-value구조로 JSONObject 포맷의 데이터와 호환 가능.
2. JSON 형태로 들어온 데이터를 각각의 key값에 맞게 파싱, 마지막 movie의 경우 JSONArray 형식으로 되어 있어 NSArray 객체로 호환.
3. NSArray로 들어온 영화정보들은 미리 생성해 놓은 MovieVO 객체의 프로퍼티에 맞게 파싱 후 list[MovieVO] 타입의 array에 저장.
