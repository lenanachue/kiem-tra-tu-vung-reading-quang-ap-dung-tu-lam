<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bài Kiểm Tra Từ Vựng</title>
<style>
:root{
  --purple-1:#f3e8ff;
  --purple-2:#e9d5ff;
  --purple-3:#c084fc;
  --purple-4:#a855f7;
  --purple-5:#7e22ce;
  --purple-dark:#581c87;
  --pink:#f0abfc;
  --card-bg:#ffffff;
  --correct:#22c55e;
  --wrong:#ef4444;
}
*{box-sizing:border-box;}
body{
  margin:0;
  font-family:'Segoe UI','Roboto',Arial,sans-serif;
  background:linear-gradient(135deg,var(--purple-1) 0%, var(--purple-2) 40%, #fdf4ff 100%);
  color:#3b0764;
  min-height:100vh;
  position:relative;
  overflow-x:hidden;
}
.floaty{
  position:fixed;
  font-size:34px;
  opacity:0.16;
  z-index:0;
  animation:float 8s ease-in-out infinite;
  pointer-events:none;
}
@keyframes float{
  0%,100%{transform:translateY(0px) rotate(0deg);}
  50%{transform:translateY(-22px) rotate(8deg);}
}
.f1{top:6%;left:4%;animation-delay:0s;}
.f2{top:14%;right:6%;animation-delay:1.5s;}
.f3{bottom:16%;left:7%;animation-delay:3s;}
.f4{bottom:6%;right:9%;animation-delay:2s;}
.f5{top:48%;left:2%;animation-delay:4s;}
.f6{top:60%;right:3%;animation-delay:2.5s;}

.wrap{
  max-width:900px;
  margin:0 auto;
  padding:28px 18px 60px;
  position:relative;
  z-index:1;
}
header{text-align:center; margin-bottom:18px;}
header h1{
  font-size:clamp(22px,4vw,30px);
  background:linear-gradient(90deg,var(--purple-5),var(--pink));
  -webkit-background-clip:text;
  background-clip:text;
  color:transparent;
  margin:0 0 6px;
}
header p{color:#6b21a8; font-size:14.5px; margin:0;}

.theory-box{
  background:#fff;
  border:2px dashed var(--purple-3);
  border-radius:16px;
  padding:16px 18px;
  margin:18px 0 26px;
  font-size:13.5px;
  color:#5b21b6;
  line-height:1.7;
}
.theory-box b{color:var(--purple-5);}
.theory-box .title{
  font-weight:700;
  color:var(--purple-5);
  font-size:15px;
  display:block;
  margin-bottom:6px;
}

.section-title{
  font-size:18px;
  color:var(--purple-dark);
  margin:26px 0 14px;
  padding-left:10px;
  border-left:5px solid var(--purple-4);
}
.section-sub{
  font-size:13px;
  color:#8b5cf6;
  margin:-10px 0 14px 15px;
  font-style:italic;
}

.q-card{
  background:var(--card-bg);
  border:2px solid var(--purple-2);
  border-left:6px solid var(--purple-4);
  border-radius:16px;
  padding:16px 18px;
  margin-bottom:14px;
  box-shadow:0 3px 10px rgba(168,85,247,0.08);
}
.q-num{
  font-weight:700;
  color:var(--purple-5);
  margin-right:6px;
}
.q-text{font-size:15px; margin-bottom:10px; line-height:1.6;}
.options{display:flex; flex-direction:column; gap:8px;}
.option{
  display:flex;
  align-items:center;
  gap:8px;
  background:var(--purple-1);
  border:1.5px solid transparent;
  border-radius:10px;
  padding:8px 12px;
  font-size:14px;
  cursor:pointer;
  transition:all .15s;
}
.option:hover{border-color:var(--purple-3);}
.option input{accent-color:var(--purple-5);}
.option.opt-correct{background:#dcfce7; border-color:var(--correct); font-weight:600;}
.option.opt-wrong{background:#fee2e2; border-color:var(--wrong);}

.blank-input{
  border:none;
  border-bottom:2.5px solid var(--purple-4);
  background:var(--purple-1);
  padding:4px 10px;
  font-size:15px;
  font-family:inherit;
  width:150px;
  text-align:center;
  border-radius:6px 6px 0 0;
  color:var(--purple-dark);
  font-weight:600;
}
.blank-input:focus{outline:none; background:#fff; border-bottom-color:var(--pink);}
.blank-input.correct{background:#dcfce7; border-bottom-color:var(--correct); color:#15803d;}
.blank-input.wrong{background:#fee2e2; border-bottom-color:var(--wrong); color:#b91c1c;}

.hint-btn{
  border:1px solid var(--purple-3);
  background:#fdf4ff;
  color:var(--purple-5);
  font-size:12px;
  padding:3px 9px;
  border-radius:10px;
  cursor:pointer;
  margin-left:8px;
}
.hint-text{font-size:12.5px; color:#9333ea; margin-top:6px; display:none;}
.answer-reveal{font-size:12.5px; color:#b91c1c; margin-top:6px; display:none;}

.check-row{
  display:flex; gap:10px; justify-content:center;
  margin:26px 0 10px; flex-wrap:wrap;
}
.btn{
  border:none; padding:12px 26px; border-radius:12px;
  font-weight:700; font-size:15px; cursor:pointer; transition:transform .15s;
}
.btn:hover{transform:translateY(-2px);}
.btn-primary{
  background:linear-gradient(90deg,var(--purple-4),var(--pink));
  color:#fff; box-shadow:0 4px 12px rgba(168,85,247,0.35);
}
.btn-secondary{background:#fff; color:var(--purple-5); border:2px solid var(--purple-3);}

.result-box{
  text-align:center; font-size:17px; font-weight:700;
  padding:16px; border-radius:14px; margin-top:18px; display:none;
}
.result-good{background:#dcfce7; color:#15803d; display:block;}
.result-mid{background:#fef9c3; color:#854d0e; display:block;}
.result-low{background:#fee2e2; color:#b91c1c; display:block;}

.history-box{
  background:#fff;
  border:2px solid var(--purple-2);
  border-radius:16px;
  padding:14px 18px;
  margin-top:16px;
  display:none;
}
.history-box.show{display:block;}
.history-box .title{font-weight:700; color:var(--purple-5); margin-bottom:8px; font-size:14.5px;}
.history-row{
  display:flex; justify-content:space-between;
  font-size:13px; color:#6b21a8;
  padding:5px 0; border-bottom:1px dashed var(--purple-2);
}
.history-row:last-child{border-bottom:none;}

.footer-note{text-align:center; color:#9333ea; font-size:12.5px; margin-top:30px; opacity:0.8;}
</style>
</head>
<body>

<div class="floaty f1">📝</div>
<div class="floaty f2">🧠</div>
<div class="floaty f3">📖</div>
<div class="floaty f4">✅</div>
<div class="floaty f5">💜</div>
<div class="floaty f6">🎓</div>

<div class="wrap">
  <header>
    <h1>🧠 Bài Kiểm Tra Từ Vựng 🧠</h1>
    <p>20 từ đã học — kiểm tra để ghi nhớ lâu hơn!</p>
  </header>

  <div class="theory-box">
    <span class="title">📌 Vì sao bài kiểm tra này được thiết kế như vậy?</span>
    • <b>Hồi tưởng chủ động (active recall):</b> Phần 2 không có ngân hàng từ — em phải tự nhớ lại từ, cách này giúp nhớ lâu hơn nhiều so với chỉ đọc lại.<br>
    • <b>Xen kẽ (interleaving):</b> Các câu hỏi trộn lẫn từ cả 2 bài đọc thay vì tách riêng, giúp não bộ phân biệt và ghi nhớ tốt hơn.<br>
    • <b>Gợi ý có kiểm soát:</b> Nếu quên, em có thể bấm nút gợi ý chữ cái đầu — chỉ dùng khi thực sự cần, vì cố nhớ trước khi xem gợi ý mới là bước quan trọng nhất.<br>
    • <b>Ôn tập giãn cách (spaced repetition):</b> Điểm số được lưu lại mỗi lần làm — em nên quay lại làm bài này sau 1–2 ngày để củng cố trí nhớ dài hạn.
  </div>

  <div class="section-title">Phần 1 — Chọn nghĩa đúng (Trắc nghiệm)</div>
  <div class="section-sub">Đọc từ, chọn nghĩa tiếng Việt chính xác nhất.</div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">1.</span>advantage</div>
    <div class="options">
      <label class="option"><input type="radio" name="q1" value="a">lợi thế, điểm thuận lợi</label>
      <label class="option"><input type="radio" name="q1" value="b">bất lợi</label>
      <label class="option"><input type="radio" name="q1" value="c">sự yên tĩnh</label>
      <label class="option"><input type="radio" name="q1" value="d">nghề nghiệp</label>
    </div>
  </div>

  <div class="q-card" data-correct="c">
    <div class="q-text"><span class="q-num">2.</span>quietness</div>
    <div class="options">
      <label class="option"><input type="radio" name="q2" value="a">giao thông</label>
      <label class="option"><input type="radio" name="q2" value="b">sự giải trí</label>
      <label class="option"><input type="radio" name="q2" value="c">sự yên tĩnh</label>
      <label class="option"><input type="radio" name="q2" value="d">dân số</label>
    </div>
  </div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">3.</span>traffic</div>
    <div class="options">
      <label class="option"><input type="radio" name="q3" value="a">giao thông, xe cộ</label>
      <label class="option"><input type="radio" name="q3" value="b">sự nghiệp</label>
      <label class="option"><input type="radio" name="q3" value="c">nông nghiệp</label>
      <label class="option"><input type="radio" name="q3" value="d">truyền thống</label>
    </div>
  </div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">4.</span>particularly</div>
    <div class="options">
      <label class="option"><input type="radio" name="q4" value="a">đặc biệt là</label>
      <label class="option"><input type="radio" name="q4" value="b">phù hợp</label>
      <label class="option"><input type="radio" name="q4" value="c">nhanh chóng</label>
      <label class="option"><input type="radio" name="q4" value="d">hiệu quả</label>
    </div>
  </div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">5.</span>career</div>
    <div class="options">
      <label class="option"><input type="radio" name="q5" value="a">sự nghiệp</label>
      <label class="option"><input type="radio" name="q5" value="b">nghề nghiệp chuyên môn</label>
      <label class="option"><input type="radio" name="q5" value="c">dân số</label>
      <label class="option"><input type="radio" name="q5" value="d">công nghiệp</label>
    </div>
  </div>

  <div class="q-card" data-correct="b">
    <div class="q-text"><span class="q-num">6.</span>rapidly</div>
    <div class="options">
      <label class="option"><input type="radio" name="q6" value="a">vẫn còn</label>
      <label class="option"><input type="radio" name="q6" value="b">một cách nhanh chóng</label>
      <label class="option"><input type="radio" name="q6" value="c">không thay đổi</label>
      <label class="option"><input type="radio" name="q6" value="d">bùng nổ</label>
    </div>
  </div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">7.</span>population</div>
    <div class="options">
      <label class="option"><input type="radio" name="q7" value="a">dân số</label>
      <label class="option"><input type="radio" name="q7" value="b">sự nghiệp</label>
      <label class="option"><input type="radio" name="q7" value="c">truyền thống</label>
      <label class="option"><input type="radio" name="q7" value="d">nông nghiệp</label>
    </div>
  </div>

  <div class="q-card" data-correct="d">
    <div class="q-text"><span class="q-num">8.</span>traditional</div>
    <div class="options">
      <label class="option"><input type="radio" name="q8" value="a">hiệu quả</label>
      <label class="option"><input type="radio" name="q8" value="b">công nghiệp</label>
      <label class="option"><input type="radio" name="q8" value="c">không thay đổi</label>
      <label class="option"><input type="radio" name="q8" value="d">thuộc về truyền thống</label>
    </div>
  </div>

  <div class="q-card" data-correct="a">
    <div class="q-text"><span class="q-num">9.</span>efficient</div>
    <div class="options">
      <label class="option"><input type="radio" name="q9" value="a">hiệu quả</label>
      <label class="option"><input type="radio" name="q9" value="b">công nghiệp</label>
      <label class="option"><input type="radio" name="q9" value="c">nông nghiệp</label>
      <label class="option"><input type="radio" name="q9" value="d">nghề nghiệp</label>
    </div>
  </div>

  <div class="q-card" data-correct="b">
    <div class="q-text"><span class="q-num">10.</span>profession</div>
    <div class="options">
      <label class="option"><input type="radio" name="q10" value="a">sự nghiệp</label>
      <label class="option"><input type="radio" name="q10" value="b">nghề nghiệp chuyên môn</label>
      <label class="option"><input type="radio" name="q10" value="c">dân số</label>
      <label class="option"><input type="radio" name="q10" value="d">truyền thống</label>
    </div>
  </div>

  <div class="section-title">Phần 2 — Điền từ (Hồi tưởng chủ động)</div>
  <div class="section-sub">Không có ngân hàng từ — cố nhớ trước khi bấm gợi ý nhé!</div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">11.</span>One <input class="blank-input" id="b11" data-answer="disadvantage"> of working night shifts is that you rarely see your family.
      <button class="hint-btn" onclick="showHint(11,'d...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint11"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">12.</span>The staff at this hotel are extremely <input class="blank-input" id="b12" data-answer="friendly"> and always smile at guests.
      <button class="hint-btn" onclick="showHint(12,'f...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint12"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">13.</span>There wasn't much <input class="blank-input" id="b13" data-answer="entertainment"> in the village, so children made their own games.
      <button class="hint-btn" onclick="showHint(13,'e...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint13"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">14.</span>This job is very <input class="blank-input" id="b14" data-answer="suitable"> for someone who loves working outdoors.
      <button class="hint-btn" onclick="showHint(14,'s...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint14"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">15.</span>After 40 years of teaching, she finally <input class="blank-input" id="b15" data-answer="retired"> last year.
      <button class="hint-btn" onclick="showHint(15,'r...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint15"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">16.</span>Despite the storm, the old bridge continued to <input class="blank-input" id="b16" data-answer="remain"> standing for another century.
      <button class="hint-btn" onclick="showHint(16,'r...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint16"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">17.</span>The city's economy <input class="blank-input" id="b17" data-answer="boomed"> after the factory opened.
      <button class="hint-btn" onclick="showHint(17,'b...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint17"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">18.</span>Even after renovations, the church's exterior looked almost <input class="blank-input" id="b18" data-answer="unchanged">.
      <button class="hint-btn" onclick="showHint(18,'u...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint18"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">19.</span>The area near the river became a busy <input class="blank-input" id="b19" data-answer="industrial"> zone full of factories.
      <button class="hint-btn" onclick="showHint(19,'i...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint19"></div>
  </div>

  <div class="q-card">
    <div class="q-text"><span class="q-num">20.</span>Most people in this region depend on <input class="blank-input" id="b20" data-answer="agriculture"> for their income.
      <button class="hint-btn" onclick="showHint(20,'a...')">💡 Gợi ý</button>
    </div>
    <div class="hint-text" id="hint20"></div>
  </div>

  <div class="check-row">
    <button class="btn btn-primary" onclick="submitTest()">📤 Nộp bài kiểm tra</button>
    <button class="btn btn-secondary" onclick="resetTest()">🔄 Làm lại</button>
  </div>

  <div id="resultBox" class="result-box"></div>
  <div id="historyBox" class="history-box">
    <div class="title">📅 Lịch sử làm bài (ôn tập giãn cách giúp nhớ lâu hơn)</div>
    <div id="historyList"></div>
  </div>

  <div class="footer-note">💜 Sai không sao — quay lại phần từ vựng, ôn lại, và làm bài lần nữa sau 1-2 ngày nhé! 💜</div>
</div>

<script>
function showHint(num, letters){
  const el = document.getElementById('hint'+num);
  el.textContent = '🔤 Gợi ý: bắt đầu bằng "' + letters + '"';
  el.style.display = 'block';
}

function normalize(str){ return str.trim().toLowerCase().replace(/\s+/g,''); }

function submitTest(){
  let correct = 0;
  const total = 20;

  // Part 1: MCQ
  for(let i=1;i<=10;i++){
    const card = document.querySelectorAll('.q-card')[i-1];
    const correctVal = card.getAttribute('data-correct');
    const selected = card.querySelector('input[name="q'+i+'"]:checked');
    card.querySelectorAll('.option').forEach(opt=>{
      opt.classList.remove('opt-correct','opt-wrong');
      const inp = opt.querySelector('input');
      if(inp.value === correctVal) opt.classList.add('opt-correct');
    });
    if(selected){
      if(selected.value === correctVal){ correct++; }
      else{
        selected.closest('.option').classList.add('opt-wrong');
      }
    }
  }

  // Part 2: fill blank
  for(let i=11;i<=20;i++){
    const inp = document.getElementById('b'+i);
    const answer = normalize(inp.getAttribute('data-answer'));
    const given = normalize(inp.value);
    inp.classList.remove('correct','wrong');
    if(given === answer){ inp.classList.add('correct'); correct++; }
    else{ inp.classList.add('wrong'); }
  }

  const resultBox = document.getElementById('resultBox');
  resultBox.classList.remove('result-good','result-mid','result-low');
  const ratio = correct/total;
  let cls, msg, emoji;
  if(ratio === 1){ cls='result-good'; emoji='🎉🌟'; msg='Tuyệt vời! Em đã nhớ hết 20 từ!'; }
  else if(ratio >= 0.7){ cls='result-mid'; emoji='👏😊'; msg='Khá tốt! Xem lại các từ sai rồi quay lại làm bài sau 1-2 ngày nhé!'; }
  else{ cls='result-low'; emoji='💪📖'; msg='Chưa sao! Ôn lại phần từ vựng rồi thử lại nha!'; }
  resultBox.classList.add(cls);
  resultBox.innerHTML = `${emoji} Đúng ${correct}/${total} câu — ${msg}`;

  // Save history
  try{
    let history = JSON.parse(localStorage.getItem('vocab_test_history') || '[]');
    const now = new Date();
    history.push({date: now.toLocaleDateString('vi-VN') + ' ' + now.toLocaleTimeString('vi-VN',{hour:'2-digit',minute:'2-digit'}), correct, total});
    if(history.length > 8) history = history.slice(history.length-8);
    localStorage.setItem('vocab_test_history', JSON.stringify(history));
    renderHistory();
  }catch(e){}

  resultBox.scrollIntoView({behavior:'smooth', block:'center'});
}

function renderHistory(){
  try{
    const history = JSON.parse(localStorage.getItem('vocab_test_history') || '[]');
    if(history.length === 0) return;
    const box = document.getElementById('historyBox');
    const list = document.getElementById('historyList');
    list.innerHTML = '';
    history.slice().reverse().forEach(h=>{
      const row = document.createElement('div');
      row.className = 'history-row';
      row.innerHTML = `<span>${h.date}</span><span>${h.correct}/${h.total} điểm</span>`;
      list.appendChild(row);
    });
    box.classList.add('show');
  }catch(e){}
}

function resetTest(){
  document.querySelectorAll('input[type=radio]').forEach(r=>r.checked=false);
  document.querySelectorAll('.option').forEach(o=>o.classList.remove('opt-correct','opt-wrong'));
  document.querySelectorAll('.blank-input').forEach(inp=>{ inp.value=''; inp.classList.remove('correct','wrong'); });
  document.querySelectorAll('.hint-text').forEach(h=>{ h.style.display='none'; h.textContent=''; });
  const resultBox = document.getElementById('resultBox');
  resultBox.classList.remove('result-good','result-mid','result-low');
  resultBox.innerHTML='';
  window.scrollTo({top:0, behavior:'smooth'});
}

renderHistory();
</script>

</body>
</html>
