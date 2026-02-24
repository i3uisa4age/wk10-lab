# 🎬 ปฏิบัติการที่ 10: Movie Database SPA -

**Movie Database** คือแอปพลิเคชัน Single Page Application (SPA) สำหรับค้นหาและดูข้อมูลภาพยนตร์

ปฎิบัติการนี้ใช้:

- **Fetch API** - ดึงข้อมูลจาก OMDB API (Real API)
- **CORS** - จัดการการขอข้อมูลข้ามโดเมน
- **SPA Structure** - สถาปัตยกรรมแอปลิเคชันแบบเดียว
- **Hash-Based Routing** - นำทางด้วย URL hash (#/)

---

## 📁 โครงสร้างไฟล์

```
lab10/
├── index.html          # ไฟล์ HTML หลัก
├── css/
│   └── style.css       # Styling ทั้งแอป
├── js/
│   ├── api.js          # Fetch API (OMDB API)
│   ├── views.js        # HTML templates
│   ├── router.js       # Hash-based routing
│   └── main.js         # Application logic
├── README.md           # ไฟล์นี้
└── SETUP.md            # คำแนะนำการตั้งค่า OMDB API
```

---

### ขั้นตอนที่ 1: ตั้งค่า OMDB API Key

1. ไปที่ https://www.omdbapi.com/apikey.aspx
2. เลือก "Free!" และใส่อีเมล
3. ตรวจสอบอีเมล และคัดลอก API key
4. เปิด `lab10/js/api.js` และแทนที่:

```javascript
API_KEY: "YOUR_OMDB_API_KEY_HERE",  // ← แล้วเปลี่ยนตรงนี้ด้วย API key ของคุณ
```

ดู [SETUP.md](SETUP.md) สำหรับคำแนะนำรายละเอียด

### ขั้นตอนที่ 2: เปิดไฟล์ HTML

```bash
# ใช้ Live Server (VS Code)
- คลิกขวาที่ index.html → "Open with Live Server"
```

### ขั้นตอนที่ 3: ไปที่ URL

```
http://localhost:5500/lab10/index.html
หรือ
http://127.0.0.1:5500/lab10/index.html
```

---

## ![screen](https://staff.informatics.buu.ac.th/~wittawas/682/88726065/lab10-screen.png)

## 🗺️ Routes (เส้นทาง)

| Route         | ชื่อหน้า     | คำอธิบาย                            |
| ------------- | ------------ | ----------------------------------- |
| `#/`          | Home         | หน้าแรกของแอป                       |
| `#/movies`    | Movie List   | รายชื่อภาพยนตร์ทั้งหมด              |
| `#/movie/:id` | Movie Detail | รายละเอียดภาพยนตร์ (เช่น #/movie/1) |
| `#/search`    | Search       | ค้นหาภาพยนตร์                       |

---

## 🧩 โมดูล (Modules)

### 📝 js/api.js

- ดึงข้อมูลจาก **OMDB API** (Real API - ต้องมี API key)
- `API.getMovies()` - ค้นหาภาพยนตร์ชื่อ "movie"
- `API.getMovieById(imdbID)` - ดึงเฉพาะรายการ (IMDb ID) พร้อม poster, director, actors
- `API.searchMovies(query)` - ค้นหาตามชื่อ
- **Caching**: เก็บข้อมูลเพื่อไม่ต้องดึง API ซ้ำ
- **Error Handling**: ตรวจสอบ API response

### 🎨 js/views.js

- HTML templates ของแต่ละหน้า
- `Views.home()` - Home page
- `Views.movieList(movies)` - รายชื่อ
- `Views.movieDetail(movie)` - รายละเอียด
- `Views.search()` - ค้นหา
- `Views.loading()` - Loading state
- `Views.notFound()` - 404 page

### 🛣️ js/router.js

- Class `Router` สำหรับจัดการ routing
- ฟัง `hashchange` event
- เปลี่ยน view ตามค่า hash
- อัปเดต active navigation link

### ⚙️ js/main.js

- Application logic
- `handleSearch()` - ยุติการค้นหา
- Initialization logging

---

## 💻 การเรนเดอร์ (Rendering Flow)

```
User clicks link
    ↓
Hash changes (#/movies)
    ↓
Router.navigate() triggered
    ↓
Shows loading state
    ↓
Fetch data via API
    ↓
Render view with data
    ↓
Update active nav link
```

---

## 🧪 ทดสอบ

### ใน Browser Console

```javascript
// ทดสอบ API
API.getMovies().then((movies) => console.log(movies));
API.getMovieById(1).then((movie) => console.log(movie));
API.searchMovies("Dark").then((results) => console.log(results));

// ทดสอบ Router
location.hash = "#/";
location.hash = "#/movies";
location.hash = "#/movie/2";
location.hash = "#/search";
```

---

## ✨ Features

| Feature           | สถานะ | อธิบาย                             |
| ----------------- | ----- | ---------------------------------- |
| Home Page         |       | แสดงหน้าแรกและปุ่มดูรายชื่อ        |
| Movie List        |       | Grid layout พร้อม poster images    |
| Movie Detail      |       | แสดง poster, director, actors      |
| Search            |       | ค้นหาภาพยนตร์แบบ real-time         |
| OMDB API          |       | เรียก real API (ต้อง API key)      |
| Navigation        |       | Hash-based routing ทำงาน           |
| Loading State     |       | แสดง "Loading..." ระหว่างดึงข้อมูล |
| Caching           |       | เก็บข้อมูลเพื่อลด API calls        |
| Error Handling    |       | จัดการสถานการณ์ error              |
| Responsive Design |       | Grid layout responsive             |

---

## 🎨 UI/UX

- **Header**: ชื่อแอปและ navigation links
- **Main Area**: แสดงเนื้อหา
- **Footer**: ข้อมูลลิขสิทธิ์
- **Colors**: Purple gradient background (#667eea, #764ba2)
- **Cards**: Hover effect สำหรับ movie cards
- **Buttons**: Styled buttons ที่ interactive

---

## 🐛 Debugging

### ถ้า routes ไม่ทำงาน

```javascript
// ตรวจเช็ก hash ใน console
console.log(window.location.hash);
```

### ถ้า data ไม่มา

```javascript
// ตรวจเช็ก API
API.getMovies().then((data) => console.table(data));
```

### ถ้า styles ไม่โหลด

- ตรวจสอบเส้นทาง CSS ใน index.html
- ตรวจสอบ console ว่ามี error

---

## 📚 เทคนิคที่ใช้

### JavaScript

- **Async/Await** - ดึงข้อมูลแบบ asynchronous
- **Promise** - จัดการการเรียก API
- **ES6 Classes** - Router class
- **Event Listeners** - hashchange, load events
- **Array Methods** - map, filter, find
- **Template Literals** - HTML templates

### HTML/CSS

- **Semantic HTML** - header, nav, main, footer
- **CSS Grid** - Movie list layout
- **Flexbox** - Navigation layout
- **CSS Transitions** - Hover effects
- **Gradient Background** - Visual appeal

---

## 🚀 Enhancement Ideas

ถ้าต้องการเพิ่มเติม:

1. **Local Storage**: บันทึก "Favorites" ไว้
2. **Sorting**: เรียงตามชื่อหรือ rating
3. **Filtering**: กรองตามปี
4. **Pagination**: แสดง movies เป็นหน้า
5. **TMDB API**: เปลี่ยนจาก OMDB เป็น TMDB (More data)
6. **Ratings**: แสดง IMDb rating ด้วย rating widget
7. **Delete/Edit**: จัดการรายการโปรด

---

## 📖 References

- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
- [MDN - Web Component](https://developer.mozilla.org/en-US/docs/Web/Web_Components)
- เอกสารเรียน: wk10-fetch-api.md, wk10-cors.md, wk10-spa.md, wk10-hash-based-routing.md

---

## 📝 Notes

- ใช้ **OMDB API** (Real API) - ต้องมี API key ฟรี
- CORS ทำงาน - OMDB รองรับ CORS headers
- Caching - ลด API calls ด้วยการเก็บข้อมูล
- Router ใช้ hash-based มี support browser back button
- Loading state ช่วยให้ผู้ใช้รู้ว่าแอปกำลังทำงาน
- ไม่มี page refresh - ทั้งหมด client-side rendering
