<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج اشتراك الوجبات</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            direction: rtl; /* لجعل النص من اليمين لليسار */
        }
        label {
            margin-top: 10px;
            display: block;
        }
        textarea {
            width: 100%;
            height: 50px;
        }
        .meal-selection {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>

<h1>نموذج اشتراك الوجبات</h1>

<form id="meal-form">
    <label for="client-name">اسم العميل:</label>
    <input type="text" id="client-name" required>

    <label for="subscription">نوع الاشتراك:</label>
    <select id="subscription" required>
        <option value="وجبة مع سناك 100 جرام">وجبة مع سناك 100 جرام</option>
        <option value="وجبتين مع سناك 100 جرام">وجبتين مع سناك 100 جرام</option>
        <option value="ثلاثة وجبات مع سناك 100 جرام">ثلاثة وجبات مع سناك 100 جرام</option>
    </select>

    <div class="meal-selection">
        <h2>اختيار الوجبات</h2>
        <p>اختر الوجبات لكل يوم من السبت إلى الخميس:</p>

        <div id="days">
            <label for="saturday">السبت:</label>
            <select id="saturday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-saturday" placeholder="ملاحظات للسبت"></textarea>

            <label for="sunday">الأحد:</label>
            <select id="sunday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-sunday" placeholder="ملاحظات للأحد"></textarea>

            <label for="monday">الاثنين:</label>
            <select id="monday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-monday" placeholder="ملاحظات للإثنين"></textarea>

            <label for="tuesday">الثلاثاء:</label>
            <select id="tuesday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-tuesday" placeholder="ملاحظات الثلاثاء"></textarea>

            <label for="wednesday">الأربعاء:</label>
            <select id="wednesday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-wednesday" placeholder="ملاحظات للأربعاء"></textarea>

            <label for="thursday">الخميس:</label>
            <select id="thursday" multiple>
                <option value="فلكس فيول بيتزا">فلكس فيول بيتزا</option>
                <option value="بيتزا بيبروني">بيتزا بيبروني</option>
                <option value="راب كباب لحم">راب كباب لحم</option>
                <option value="راب كباب دجاج">راب كباب دجاج</option>
            </select>
            <textarea id="note-thursday" placeholder="ملاحظات الخميس"></textarea>
        </div>
    </div>

    <button type="button" onclick="submitForm()">إرسال الطلب</button>
</form>

<script>
    function submitForm() {
        const clientName = document.getElementById("client-name").value;
        const subscription = document.getElementById("subscription").value;

        const meals = {
            "السبت": {
                meal: Array.from(document.getElementById("saturday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-saturday").value
            },
            "الأحد": {
                meal: Array.from(document.getElementById("sunday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-sunday").value
            },
            "الاثنين": {
                meal: Array.from(document.getElementById("monday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-monday").value
            },
            "الثلاثاء": {
                meal: Array.from(document.getElementById("tuesday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-tuesday").value
            },
            "الأربعاء": {
                meal: Array.from(document.getElementById("wednesday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-wednesday").value
            },
            "الخميس": {
                meal: Array.from(document.getElementById("thursday").selectedOptions).map(option => option.value),
                note: document.getElementById("note-thursday").value
            }
        };

        const message = `
            اسم العميل: ${clientName}
            نوع الاشتراك: ${subscription}
            الوجبات:
            ${Object.entries(meals).map(([day, {meal, note}]) => `${day}: ${meal.join(", ")} \n  ملاحظات: ${note}`).join("\n")}
        `;

        const whatsappNumber = "+966508821819";
        const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;

        window.open(whatsappUrl);
    }
</script>

</body>
</html>
