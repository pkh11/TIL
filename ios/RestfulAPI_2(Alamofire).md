## Alamofire 이용 

Alamofire : ios에서 사용하는 Swift 기반 HTTP 통신 라이브러리

(사전에 pod 파일에 alamofire 라이브러리 추가)

```Swift
import Alamofire
```
Alamofire request 함수
```Swift
Alamofire.request(
            url, 
            method: .get, // Get 방식
            parameters: ["version":"1","page":"\(self.page)","count":"10","genreId":"","order":"releasedateasc"],
            // 파라미터 전송시, Post 방식의 경우 VO타입으로 보낼 수 있음. 
            encoding: URLEncoding.default, 
            headers: ["Content-Type":"application/json", "Accept":"application/json"])
         .validate()
         .responseJSON { (response) in
                // json 형태로 받은 데이터 값을 딕셔너리 형태로 저장
                let str = response.result.value as! NSDictionary
                
                // 데이터 파싱
                let hoppin = str["hoppin"] as! NSDictionary
                let movies = hoppin["movies"] as! NSDictionary
                let movie = movies["movie"] as! NSArray
              
              
              // ....
}
```


