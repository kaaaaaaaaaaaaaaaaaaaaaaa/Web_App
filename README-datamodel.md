# Yêu cầu cho data model


---
## Tính năng chi tiết
###  Tính năng cho người dùng 
   - Đặt phòng
   - Bình luận 
###  Tính năng cho admin 

- Tài khoản
   - Đăng ký 
   - Đăng nhập
   - Sửa tài khoản

- Booking 
   - Thêm phòng
   - Xem phòng
   - Sửa phòng
   - Xóa phòng
   
- Blogs
   - Thêm blog
   - Xem blog
   - Sửa blog
   - Xóa blog

## Mô hình của database
---
Để giải quyết bài toán trên, database của app sẽ cần  *collections*:

### Collection "User"

Ví dụ:

```js
{
    "_id": ObjectId("523b1153a2aa6a3233a913f8"),
    "userName": "nguyenvana",
    "passworld": "123456789", // cần phải encrypt password
    "email": "nguyenvana@gmail.com",
    "firstName": "A",
    "lastName": "Nguyễn Văn"
    "avatar": "http://www.photos.com/nguyenvana.jog",
    "description": "Sinh vien FUNIX",
    "facebookAcc": "nguyenvana"
}
```

### Collection "Posts"

```js
{
    "_id": ObjectId("634b1153a2aa6a3233a914g9"),
    "title": "Kinh nghiệm sử dụng GIT",
    "content": "Đây là nội dung của bài viết. Blah blah ...",
    "userID": ObjectId("523b1153a2aa6a3233a913f8")
}
```

### Collection "Comments"

```js
{
    {
        "content": "Bài này viết tốt quá",
        "authorID": ObjectId("745b1153a2aa6a3233a915h0"),
        "postID": ObjectId("235b1153a2aa6a3233a911a4"),
    },
    {
        "content": "Cần bổ sung thêm về ...",
        "authorID": ObjectId("412b1153a2aa6a3233a9132e7"),
        "postID": ObjectId("412b1153a2aa6a3233a913ada1"),
    }
},
```

### Collection "Likes"

```js
{
    "ownerID": ObjectId("412b1153a2aa6a3233a9132e7"),
    "_type": "Post", // "post" hoặc "comment"
    "target_id": ObjectId("412b1153a2aa6a3233a9132e7"),
    "count": 10// "post": [0,50], "comment": [0,1]
}
```

## Bảng liệt kê HTTP routes và verbs:
---

| Resources/Session    | Actions     | Routes     | Methods | Description | Parameters |
|---        |---        |---        |---        |---        |---                |
|admin  | index |/admin |GET    | hiện toàn bộ admin |      |
|       | add-account  |/admin/:id |POST    |hiện profile của user |    |
|       | view-account|/admin | GET      | hiện toàn bộ account admin      |   |
|       |edit-account|/admin | PUT  | sửa tài khoản  |   |
|       | add-booking |/admin/:id |POST    |thêm thông tin booking         |    |
|       | view-booking|/admin | GET      | xem thông tin booking     |   |
|       |edit-booking|/admin | PUT  | sửa thông tin booking   |   |
|       | add-blog |/admin/:id |POST    |thêm một blog|    |
|       | view-blog|/admin | GET      | xem blog     |   |
|       |edit-blog|/admin | PUT  | Sửa một blog  |   |
|login  |login  |/login     |POST   |                       |   |
|logout |logout |/logout    |DELTE  |                       |   |
|forgot password |reset password |/forgot-password|PUT      |   |



Lưu ý: Xem xét thay HTTP bằng HTTP**s** để đảm bảo bảo mật thông tin

### Xác thực User:

- Xem xét sử dụng Passport hoặc Stormpath

### Bài tham khảo:

- [RESTful API Cho Người Bắt Đầu](https://www.codehub.vn/RESTful-API-Cho-Nguoi-Bat-Dau)
- [RESTful API Designing guidelines — The best practices](https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9)
