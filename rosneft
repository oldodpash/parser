import requests
import time
import json
import Captcha_solver


def check(data, t):
    start = time.time()
    if t != 'phone':
        return {'status': 'not_used', 'desc': 'only_phone_check', 'time': time.time() - start}
    h_1 = {
        'Accept': '*/*',
        'Accept-Encoding': 'gzip, deflate, br',
        'Accept-Language': 'ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7',
        'Connection': 'keep-alive',
        'Content-Type': 'application/json',
        'Cookie': '_ga=GA1.2.856535649.1618558860; _ym_uid=1618558860295704177; _ym_d=1618558860; regionId=0jIWVSR2ODFf6cNGBRf13g; regionName=%u041C%u043E%u0441%u043A%u0432%u0430%20%u0438%20%u041C%u041E; _sub_upd=1; _gid=GA1.2.497931348.1619045991; _ym_isad=2; host=c1f37f6bad49; antiforXX=CfDJ8CsFb1k_PZJGtTeA48UEpFIbvaYYIQi7pMC_tzCMlkDvo1of7msaUBNMJH3ceaSlYs-NGQfAByrFBIgD_xkHaagsWsdxbrB2foQzln_5y0BiaLVbBbywRuAT_TOwNtmYQmkK2k5VkxyhS7xgsnOK-rg; wizardToken=e25a172f-f457-44d8-af95-73b31e415711; _gat=1',
        'DNT': '1',
        'Host': 'komandacard.ru',
        'Referer': 'https://komandacard.ru/',
        'sec-ch-ua': '"Google Chrome";v="89", "Chromium";v="89", ";Not A Brand";v="99"',
        'sec-ch-ua-mobile': '?0',
        'Sec-Fetch-Dest': 'empty',
        'Sec-Fetch-Mode': 'cors',
        'Sec-Fetch-Site': 'same-origin',
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.128 Safari/537.36',
        'X-Requested-With': 'XMLHttpRequest',
    }
    i = str(round(time.time()))
    r = requests.get('https://komandacard.ru/account/login?_=' + i, headers=h_1)
    rvt = r.text.split('__RequestVerificationToken" type="hidden" value="')[1].split('"')[0]

    url = 'https://komandacard.ru/account/passwordrestore'
    r_k = Captcha_solver.rucaptcha_recaptcha_v2('6LejgioUAAAAAK6ZVEm_o8YhLHpnBil1J-hrPQnB', url)

    data = {
        "GoForward": 'true', "Data": [{"name": "Phone", "value": f"+7 {data[1::]}"}, {"name": "g-recaptcha-response",
                                                                                      "value": r_k},
                                      {"name": "Captcha",
                                       "value": r_k}]
    }
    headers = {
        'Accept': '*/*',
        'Accept-Encoding': 'gzip, deflate, br',
        'Accept-Language': 'ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7',
        'Connection': 'keep-alive',
        'Content-Length': '1193',
        'Content-Type': 'application/json',
        'Cookie': '_ga=GA1.2.856535649.1618558860; _ym_uid=1618558860295704177; _ym_d=1618558860; regionId=0jIWVSR2ODFf6cNGBRf13g; regionName=%u041C%u043E%u0441%u043A%u0432%u0430%20%u0438%20%u041C%u041E; _sub_upd=1; _gid=GA1.2.497931348.1619045991; _gat=1; _ym_isad=2; host=c1f37f6bad49; antiforXX=CfDJ8CsFb1k_PZJGtTeA48UEpFIbvaYYIQi7pMC_tzCMlkDvo1of7msaUBNMJH3ceaSlYs-NGQfAByrFBIgD_xkHaagsWsdxbrB2foQzln_5y0BiaLVbBbywRuAT_TOwNtmYQmkK2k5VkxyhS7xgsnOK-rg; wizardToken=956f16a9-819d-47af-aa88-a2b32c9d9ff7',
        'DNT': '1',
        'Host': 'komandacard.ru',
        'Origin': 'https://komandacard.ru',
        'Referer': 'https://komandacard.ru/',
        'RequestVerificationToken': rvt,
        'sec-ch-ua': '"Google Chrome";v="89", "Chromium";v="89", ";Not A Brand";v="99"',
        'sec-ch-ua-mobile': '?0',
        'Sec-Fetch-Dest': 'empty',
        'Sec-Fetch-Mode': 'cors',
        'Sec-Fetch-Site': 'same-origin',
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.128 Safari/537.36',
        'X-Requested-With': 'XMLHttpRequest',
    }
    r = requests.post(url, data=json.dumps(data), headers=headers)
    if '&#x41F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x442;&#x435;&#x43B;&#x44C; &#x43D;&#x435; &#x441;&#x443;&#x449;&#x435;&#x441;&#x442;&#x432;&#x443;&#x435;&#x442;!' in r.text:
        return {'status': 'ok', 'desc': '-', 'time': time.time() - start}
    elif '&#x41F;&#x440;&#x435;&#x432;&#x44B;&#x448;&#x435;&#x43D;&#x43E; &#x43A;&#x43E;&#x43B;&#x438;&#x447;&#x435;&#x441;&#x442;&#x432;&#x43E; &#x43F;&#x43E;&#x43F;&#x44B;&#x442;&#x43E;&#x43A; &#x437;&#x430;&#x43F;&#x440;&#x43E;&#x441;&#x430; &#x43A;&#x43E;&#x434;&#x430;. &#x41F;&#x43E;&#x43F;&#x440;&#x43E;&#x431;&#x443;&#x439;&#x442;&#x435; &#x43F;&#x43E;&#x437;&#x436;&#x435;.' in r.text:
        return {'status': 'error', 'desc': 'WA', 'time': time.time() - start}
    else:
        return {'status': 'ok', 'desc': '+', 'time': time.time() - start}
