<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>اصلاح کانفیگ‌های V2Ray</title>
    <meta name="description" content="ابزاری برای اصلاح کانفیگ‌های V2Ray">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@400;500;700&display=swap" rel="stylesheet">
    <link href="assets/css/style.css?v=1.0.0" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand navbar-dark bg-primary">
        <div class="container">
            <a class="navbar-brand me-0" href="https://seramo.github.io/v2ray-config-modifier/">اصلاح کانفیگ</a>
            <ul class="navbar-nav px-0">
                <li class="nav-item">
                    <a class="nav-link" href="https://youtu.be/J9g1kbdW8Oc/" target="_blank">آموزش</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link ps-0" href="https://github.com/seramo/v2ray-config-modifier/" target="_blank">گیت‌هاب</a>
                </li>
            </ul>
        </div>
    </nav>
    <div class="container mt-5">
        <div class="row">
            <div class="col-12">
                <div class="alert" role="alert" id="messageBox" style="display: none;">
                    <span id="messageText"></span>
                </div>
            </div>

            <div class="col-12">
                <label for="inputConfig" class="form-label">کانفیگ</label>
                <input type="text" id="inputConfig" class="form-control" placeholder="vless یا vmess یا trojan" dir="ltr">

            </div>

            <div class="col-12 mt-3">
                <label for="inputType" class="form-label">نوع ورودی</label>
                <select id="inputType" class="form-control" onchange="toggleInputFields()">
                    <option value="cidr">رنج آی پی</option>
                    <option value="list">لیست آی پی</option>
                </select>
            </div>

            <div class="col-12 mt-3" id="cidrFields">
                <label for="ipRange" class="form-label">رنج آی پی (CIDR)</label>
                <button onclick="loadIPRanges('cloudflare')" class="badge bg-cloudflare border-0 me-1">کلودفلر</button>
                <button onclick="loadIPRanges('gcore')" class="badge bg-gcore border-0 me-1">جی‌کور</button>
                <button onclick="loadIPRanges('fastly')" class="badge bg-fastly border-0 me-1">فستلی</button>
                <textarea id="ipRange" class="form-control" rows="4" placeholder="هر رنج آی پی در یک خط" dir="ltr"></textarea>

                <label for="outputCount" class="form-label mt-3">تعداد خروجی‌ها</label>
                <select id="outputCount" class="form-control">
                    <option value="10000">10000</option>
                    <option value="20000">20000</option>
                    <option value="30000">30000</option>
                    <option value="40000">40000</option>
                    <option value="50000">50000</option>
                    <option value="unlimited">بدون محدودیت</option>
                </select>
            </div>

            <div class="col-12 mt-3" id="listFields" style="display: none;">
                <label for="ipList" class="form-label">لیست آی .پی‌</label>
                <textarea id="ipList" class="form-control" rows="8" placeholder="هر آی پی در یک خط" dir="ltr"></textarea>
            </div>

            <div class="col-12 mt-4">
                <button onclick="generateConfigs()" class="btn btn-primary">تولید کانفیگ‌ها</button>
                <button onclick="copyToClipboard()" class="btn btn-secondary px-4" id="copyButton" style="display: none;">کپی</button>
                <button onclick="downloadOutput()" class="btn btn-success px-4" id="downloadButton" style="display: none;">دانلود</button>
            </div>
        </div>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ipaddr.js/2.0.1/ipaddr.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/js-base64@3.7.7/base64.min.js"></script>
    <script src="assets/js/script.js?v=1.0.1"></script>
</body>
</html>
