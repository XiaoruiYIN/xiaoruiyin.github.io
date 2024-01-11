<a href="https://www.norange555.com/variety05/">2023年09月</a>

<a href="https://www.norange555.com/variety06/">2023年10&11月</a>

<a href="https://www.norange555.com/2023final/">2023年12月</a>

<a href="https://www.norange555.com/diary/202401">2024年01月</a>

<select id="year" name="year" onchange="updateMonthOptions()">
        <option value="2023">2023</option>
        <option value="2024">2024</option>
</select>
<label for="year">年</label>

    
<select id="month" name="month" onchange="generateDays()">
        <option value="00">00</option>
</select>
<label for="month">月</label>

<select id="day" name="day">
        <option value="00">00</option>
</select>
<label for="day">日</label>

<button onclick="targetdate()">Search</button>

<script>
function updateMonthOptions() {
        var yearSelect = document.getElementById("year");
        var monthSelect = document.getElementById("month");
            
        monthSelect.innerHTML = '';

            // 如果年份是2023年，则只显示09到12月
        if (yearSelect.value === '2023') {
                for (var i = 9; i <= 12; i++) {
                    var month = i < 10 ? '0' + i : '' + i;
                    var option = document.createElement("option");
                    option.value = month;
                    option.text = month;
                    monthSelect.add(option);
                }
            } else {
                for (var i = 1; i <= 12; i++) {
                    var month = i < 10 ? '0' + i : '' + i;
                    var option = document.createElement("option");
                    option.value = month;
                    option.text = month;
                    monthSelect.add(option);
                }
            }
            generateDays();
        }

function targetdate() {
        var year = document.getElementById('year').value;
        var month = document.getElementById('month').value;
        var day = document.getElementById('day').value;

        var M0nth = month.charAt(0) === '0' ? month.charAt(1) : month;
        var d0ay = day.charAt(0) === '0' ? day.charAt(1) : day;

        var url = 'https://www.norange555.com/diary/' + year + month + '#' + M0nth + '月' + d0ay + '日' ;

        window.location.href = url;
        }
        
function generateDays() {
        var monthSelect = document.getElementById('month');
        var daySelect = document.getElementById('day');
        var selectedMonth = parseInt(monthSelect.value, 10);

        daySelect.innerHTML = '';

        var daysInMonth = getDaysInMonth(selectedMonth);

        for (var i = 1; i <= daysInMonth; i++) {
                var day = i < 10 ? '0' + i : '' + i;
                var option = document.createElement("option");
                option.value = day;
                option.text = day;
                daySelect.add(option);
                }
        }



function getDaysInMonth(month) {
        switch (month) {
                case 1: // January
                case 3: // March
                case 5: // May
                case 7: // July
                case 8: // August
                case 10: // October
                case 12: // December
                    return 31;
                case 4: // April
                case 6: // June
                case 9: // September
                case 11: // November
                    return 30;
                case 2: // February
                    var year = new Date().getFullYear();
                    return (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0)) ? 29 : 28;
                default:
                    return 0;
            }
        }


updateMonthOptions();
    </script>