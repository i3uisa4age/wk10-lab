# 🎬 Movie Database - ตั้งค่า OMDB API

## 📋 ขั้นตอนการตั้งค่า

### ขั้นตอนที่ 1: สมัครสมาชิก OMDB API

1. ไปที่ https://www.omdbapi.com/apikey.aspx
2. เลือก "Free!" (ฉบับฟรี 1,000 requests/day)
3. ใส่ email ของคุณ
4. ตรวจสอบ email และคลิก confirm
5. คุณจะได้ API key โดยอัตโนมัติ

### ขั้นตอนที่ 2: ใส่ API Key ในโค้ด

1. เปิดไฟล์ `lab10/js/api.js`
2. หาบรรทัด:

```javascript
API_KEY: "YOUR_OMDB_API_KEY_HERE",
```

3. แทนที่ด้วย API key ของคุณ (ตัวอย่าง):

```javascript
API_KEY: "a1b2c3d4",
```

### ขั้นตอนที่ 3: ทดสอบ

1. เปิด index.html ใน browser
2. ไปที่ `#/movies`
3. ถ้าข้อมูลขึ้นมา แสดงว่าสำเร็จ! ✅

---

## ⚠️ ข้อเตือน

### CORS Error?

```
Access to XMLHttpRequest blocked by CORS policy
```

**วิธีแก้**: OMDB API รองรับ CORS ตัวอักษร API key ต้องถูกต้อง

### ไม่ได้ข้อมูล?

```javascript
// ตรวจสอบใน Console
API.getMovies().then(console.log);
```

### ข้อมูลแสดงเป็น "N/A"?

- API key ของคุณแก่ไปแล้ว (หมดอายุ)
- ควรสร้าง API key ใหม่

---

## 🔍 ทดสอบ API ใน Console

```javascript
// 1. ดึงรายชื่อภาพยนตร์
API.getMovies().then((movies) => console.table(movies));

// 2. ค้นหา
API.searchMovies("Inception").then((results) => console.table(results));

// 3. ดึงรายละเอียด (ต้องใช้ IMDb ID)
API.getMovieById("tt1375666").then(console.log);
```

---

## 📊 ข้อมูล OMDB API

### Response Format

```json
{
  "Title": "Inception",
  "Year": "2010",
  "imdbID": "tt1375666",
  "Type": "movie",
  "Poster": "https://m.media-amazon.com/images/...",
  "Plot": "A skilled thief who steals corporate secrets...",
  "Director": "Christopher Nolan",
  "Actors": "Leonardo DiCaprio, Ellen Page, Joseph Gordon-Levitt",
  "Genre": "Action, Sci-Fi, Thriller",
  "imdbRating": "8.8"
}
```

### Limitations (ข้อจำกัด)

- Free plan: 1,000 requests/day
- Response ช้ากว่า Mock data
- บางครั้งขาดรูปภาพ (Poster)

---

## 🚀 Tips

1. **Caching**: ใช้ cache เพื่อลด API calls
2. **Error Handling**: ตรวจสอบ `Response` field
3. **Rate Limiting**: ใช้ throttling สำหรับ search
4. **Placeholder**: ใช้ placeholder image ถ้าไม่มี poster

---

## 📚 Reference

- [OMDB API Documentation](https://www.omdbapi.com/)
- [IMDb ID search](https://www.imdb.com)

---

## ✅ Checklist

- [ ] สมัครสมาชิก OMDB API
- [ ] ได้ API key
- [ ] ใส่ API key ใน api.js
- [ ] ทดสอบดึงข้อมูล
- [ ] แสดงภาพยนตร์ได้
- [ ] ค้นหาทำงาน
- [ ] รายละเอียดแสดง poster

---
