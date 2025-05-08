# -
電車を使用する場合の交通費計算が可能です。
<form id="fare-form">
  <label>出発駅：<input type="text" id="from" required></label><br>
  <label>到着駅：<input type="text" id="to" required></label><br>
  <button type="submit">運賃を計算</button>
</form>
<div id="result"></div>
const fares = {
  "新宿-渋谷": 200,
  "新宿-池袋": 160,
  "渋谷-上野": 220
};

const commuterPass = ["新宿", "池袋"]; // 定期区間

document.getElementById("fare-form").addEventListener("submit", function(e) {
  e.preventDefault();
  const from = document.getElementById("from").value.trim();
  const to = document.getElementById("to").value.trim();
  const result = document.getElementById("result");

  if (commuterPass.includes(from) && commuterPass.includes(to)) {
    result.textContent = "定期区間内の移動です。運賃は 0 円です。";
    return;
  }

  const fare = fares[`${from}-${to}`] || fares[`${to}-${from}`];
  result.textContent = fare !== undefined ? `運賃は ${fare} 円です。` : "運賃情報が見つかりません。";
});
<style>
  body { font-family: sans-serif; padding: 2rem; }
  input, button { padding: 0.5rem; margin: 0.5rem 0; }
  #result { margin-top: 1rem; font-weight: bold; }
</style>
