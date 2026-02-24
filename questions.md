# ❓ คำถามวัดความเข้าใจ - Lab10: Movie Database SPA

---

## 📚 เรื่อง 1: Fetch API และ HTTP Requests

1. ฟังก์ชัน `fetch()` ใช้ส่ง HTTP request ประเภทไหนเป็นค่าเริ่มต้น
2. เหตุใดจึงต้องใช้ `.json()` หลังจาก `fetch()` แม้ว่า response ส่งกลับมาแล้ว
3. API response ของ OMDB มี Error handling อย่างไร (ให้ยกตัวอย่างจากโค้ด)
4. ถ้า API key ผิด จะได้ข้อมูลเป็นอะไร และควรตรวจสอบอย่างไร
5. ฟังก์ชัน `API.getMovies()` ดึงข้อมูลภาพยนตร์กี่เรื่อง และค้นหาคำว่าอะไร
6. ความแตกต่างระหว่าง `API.getMovies()` กับ `API.searchMovies()` คืออะไร
7. ฟังก์ชัน `API.getMovieById()` ใช้พารามิเตอร์อะไรในการค้นหาภาพยนตร์เรื่องเดี่ยว
8. ทำไม OMDB search response ไม่มี rating แต่ detail response มี
9. URL ของ OMDB API ในโค้ดชี้ไปยังเซิร์ฟเวอร์ไหน (ให้ดูจาก `BASE_URL`)
10. ฟังก์ชัน `API.searchMovies()` จะส่งอะไรกลับมา ถ้า `query` เป็นว่างหรือ null

---

## 🎨 เรื่อง 2: SPA และ Hash-based Routing

1. SPA ย่อมาจากคำอะไร และมีข้อดีอย่างไรกว่า Traditional Web
2. Hash-based routing เมื่อเปลี่ยน URL hash จะทำให้ browser reload หน้าหรือไม่
3. Route `#/movie/:id` ใช้ตัวแปร `:id` ประเภทอะไร (ยกตัวอย่าง imdbID จริง)
4. ฟังก์ชัน `navigate()` จะถูกเรียกใช้ เมื่อเกิดเหตุการณ์ใดสองครั้ง
5. คำสั่ง `hash.slice(2)` ทำไมถึงต้องตัด 2 ตัวอักษร (ตัดอะไรออก)
6. ในโค้ด router ถ้า path มีค่าเป็น `#/movie/tt1375666` จะถูก split เป็น parts อะไรบ้าง
7. โค้ดที่จะแสดงใน `appDiv.innerHTML` มาจาก switch case กี่กรณี และมีกรณีไหนบ้าง
8. ฟังก์ชัน `updateNavigation()` ทำหน้าที่อะไร (ให้อธิบายการเปลี่ยนแปลง CSS class)
9. ถ้า user ไปที่ route ที่ไม่มีใน switch case จะแสดงอะไร
10. Event listener `hashchange` จะถูก trigger เมื่อ URL เปลี่ยนเป็น `#/movies` หรือไม่

---

## 💾 เรื่อง 3: API Caching และ Performance

1. วัตถุประสงค์ของ `API.cache` object คืออะไร
2. ฟังก์ชัน `getMovies()` จะตรวจสอบ cache ก่อนหรือหลังจาก fetch
3. Cache key สำหรับภาพยนตร์ คืออะไร (ดูจาก `this.cache.movies`)
4. ถ้าภาพยนตร์มีข้อมูลใหม่ออกมา cache เก่าจะลบออกอัตโนมัติหรือไม่
5. ประโยชน์ของการใช้ cache คืออะไร (ยกเหตุผล 2 ประการ)
6. ปัญหาเมื่อใช้ cache คืออะไร และแก้ไขอย่างไร
7. Cache ของ movie detail เก็บด้วย key ไหน (imdbID หรือ title)
8. ถ้า user ค้นหา "Inception" สองครั้ง จะใช้ API ทั้งสองครั้งหรือไม่
9. การรีเซ็ต cache ทำได้อย่างไร (ถ้าต้องการข้อมูลใหม่)
10. Cache มีพื้นที่เก็บข้อมูลจำกัดหรือไม่ ควรมี strategy สำหรับการลบหรือไม่

---

## 🔗 เรื่อง 4: CORS และ Cross-Origin Requests

1. CORS ย่อมาจากคำอะไร และเหตุใดจึงมี CORS policy
2. Browser จะบล็อก request ข้ามโดเมน (cross-origin) ด้วยเหตุผลใด
3. OMDB API รองรับ CORS หรือไม่ ยกหลักฐานจากการทำงาน
4. ความแตกต่างระหว่าง same-origin และ cross-origin request คืออะไร
5. เมื่อเกิด CORS error ข้อความจะเป็นแบบไหน (ยกตัวอย่าง)
6. Server ต้องส่ง HTTP header ไหนเพื่ออนุญาต CORS request
7. `fetch()` API จะส่ง CORS preflight request (OPTIONS) เมื่อไร
8. API key ใน URL ของ OMDB API มีประโยชน์ต่อ CORS policy หรือไม่
9. ถ้า API ไม่รองรับ CORS จะใช้วิธีแก้ไขไหน (JSONP, Proxy, etc.)
10. CORS error ส่งผลต่อการแสดงผลหน้าเว็บหรือไม่ (Network tab vs Console)

---

## 🎯 เรื่อง 5: DOM Manipulation และ Events

1. Element `#app` ใช้เก็บอะไร และทำไมถึงเลือก `innerHTML` แทน `textContent`
2. Event listener `click` ที่ใช้ใน movie card ทำหน้าที่อะไร (ดูจาก `onclick`)
3. Movie card ใช้ onclick attribute แทน addEventListener ทำไม
4. ฟังก์ชัน `handleSearch()` จะถูกเรียกใช้เมื่อเกิดเหตุการณ์ใด
5. ฟังก์ชัน `handleSearch()` จำเป็นต้องเรียก `Views.loading()` ทำไม
6. การแสดงรูปภาพในการ์ด ถ้าไม่มี poster จะแสดงอะไรแทน
7. Placeholder URL `via.placeholder.com` ใช้ทำไม
8. Navigation link ที่มี class `active` จะถูกเลือกด้วย CSS rule ไหน
9. Search results จะแสดงใน element ไหน (ยกตัวอย่าง ID)
10. ฟังก์ชัน `updateNavigation()` จะอัปเดต class ให้ element ไหนบ้าง

---

## ⏳ เรื่อง 6: Async/Await และ Promise

1. `async function` คืออะไร และมีข้อดีกว่า `.then()` หรือไม่
2. Keyword `await` จะทำให้โปรแกรมทำอะไร (halts execution หรือไม่)
3. ฟังก์ชัน `API.getMovies()` เรียกใช้ `async` ทำไม
4. ฟังก์ชัน `navigate()` ใช้ `async` และ `await` อย่างไร
5. Try-catch block ใน `API.getMovies()` จะจับ error ประเภทไหน
6. ถ้า `await fetch()` fail จะเกิดอะไร (ให้อธิบาย error handling)
7. Promise chain (`.then().catch()`) ส่วนไหนเหมือน async/await
8. Callback function `handleSearch()` ข้างใน `onkeyup` เป็น promise หรือไม่
9. ฟังก์ชัน `navigate()` await ทั้ง `getMovies()`, `getMovieById()`, `searchMovies()` ทำไม
10. ถ้า API response ช้า user จะเห็นอะไรขณะรอ (ให้อธิบายจาก Views.loading())

---

## 🛠️ เรื่อง 7: Data Transformation และ Formatting

1. OMDB API response ของ search มี fields ไหนบ้าง (ยกตัวอย่าง 3 fields)
2. ฟังก์ชัน `.slice(0, 5)` ใน `getMovies()` ทำอะไร
3. เหตุใดจึงต้อง `.map()` OMDB format มาเป็น format ของเรา
4. Rating ในการ์ด 0 ทำไม แต่ detail page แสดง 8.8 (ให้อธิบายจากข้อมูล OMDB)
5. `parseInt(movie.Year)` และ `parseFloat(data.imdbRating)` ทำหน้าที่อะไร
6. Poster image ที่ "N/A" จะถูกแทนที่ด้วยอะไร
7. Movie object ของเรามี fields ไหนบ้าง (ยกตัวอย่างอย่างน้อย 5 fields)
8. IMDb ID ที่ใช้คือ imdbID หรือเป็นตัวเลขอื่น
9. Genre และ Actors จะปรากฏที่หน้าไหนในแอป (detail page หรือ list page)
10. Plot ใน API response จะแสดงใน UI ที่ไหน (ให้อธิบายตำแหน่ง)

---

## ✅ เรื่อง 8: Testing และ Debugging

1. Console.log ที่ใช้ใน main.js แสดงข้อมูลอะไร
2. ถ้า movie ไม่โหลด ควรตรวจสอบจาก browser tools ที่ไหนอย่างไร
3. Network tab จะแสดง API request ที่ fail หรือ success ได้ยังไง
4. Console error "API Error: ..." มาจากการตรวจสอบอะไร
5. ถ้า API key ผิด OMDB จะส่ง Response ที่เป็น "False" คืออะไร
6. `handleSearch()` ควรทดสอบด้วยการค้นหาคำไหนในแอป
7. Browser DevTools ส่วนไหนสำคัญสำหรับ debug async/await
8. ตรวจสอบความเร็ว API response (cache หรือ fetch) ทำไง
9. การค้นหา "movie" ควรคืนภาพยนตร์กี่เรื่อง (ยกตัวอย่างสอง-สามเรื่อง)
10. ถ้า search ไม่แสดงผลลัพธ์ ให้เช็ค API response ใน console ด้วยคำสั่งไหน

---

## 📱 เรื่อง 9: CSS และ UI/UX

1. Movie card layout ใช้ CSS ตัวไหน (Grid หรือ Flexbox)
2. `grid-template-columns: repeat(auto-fill, minmax(300px, 1fr))` ทำอะไร
3. Transition `transform 0.3s` ใน `.movie-card:hover` ทำอะไร
4. Placeholder image URL ใช้เพื่อจุดประสงค์ใด
5. Navigation link ที่ `active` จะมี background color มีสีไหน
6. Movie detail page แสดงภาพและข้อมูลในรูปแบบไหน (side-by-side หรือ top-bottom)
7. Loading state จะแสดง emoji อะไร และนี่สำคัญทำไม
8. `box-shadow` ที่ใช้ใน movie detail poster ทำอะไร
9. Responsive design: ถ้า screen แคบ movie grid จะมีการ์ดกี่คอลัมน์
10. Footer ของแอปจะแสดงองค์ประกอบไหนบ้าง

---

## 🔐 เรื่อง 10: Security และ Best Practices

1. API key ไว้ใน client-side code มีความเสี่ยงหรือไม่ เหตุใด
2. วิธีแก้ไข security issue ของ API key คืออะไร
3. OMDB API มีการจำกัด rate limit หรือไม่ (ฟรี account ได้กี่ requests)
4. Error handling ควรมี try-catch หรือเพียง `.catch()` ก็พอ
5. Input validation ของการค้นหา ควรตรวจสอบอะไรบ้าง
6. Script tag order ใน HTML มีความสำคัญ (api.js ก่อน main.js) ทำไม
7. `console.error()` ใช้ในไหนบ้าง และควรแสดงให้ user เห็นหรือไม่
8. Sensitive data (API key) ไม่ควรโปรแกรมใน source code แต่ดึงจากไหน
9. HTTPS จำเป็นสำหรับคำขอ OMDB API หรือไม่
10. Browser security policy จะบล็อก request ไปยัง HTTP endpoint หรือไม่ (OMDB uses HTTPS)

---
