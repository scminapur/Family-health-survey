# Family Health Survey Android — પ્રારંભિક પ્રોજેક્ટ

આ Android Studio પ્રોજેક્ટ આપેલી ZIP માંથી મળેલા Google Apps Script (`Code.gs`, `Index.html`) ને સીધો Android APKમાં કૉપી કરતો નથી. મૂળ સિસ્ટમ `google.script.run` અને `SpreadsheetApp.getActiveSpreadsheet()` પર આધારિત છે, એટલે તે Google Sheet સાથે જોડાયેલ Apps Script Web App તરીકે deploy થયેલું હોવું જરૂરી છે.

## પહેલાં Google Sheets જોડાણ તૈયાર કરો
1. તમારી મૂળ Google Sheet ખોલો.
2. Extensions → Apps Script ખોલો.
3. ZIPમાંથી `Code.gs` નો કોડ `Code.gs` માં અને `Index.html` નો કોડ `Index.html` નામની HTML ફાઇલમાં મૂકો.
4. `setupSheet` function ચલાવો અને permissions મંજૂર કરો. મૂળ ડેટાની બેકઅપ રાખો.
5. Deploy → New deployment → Web app પસંદ કરો.
6. Execute as: Me પસંદ કરો. Who has access માં તમારી સંસ્થાની ગોપનીયતા નીતિ મુજબ સૌથી મર્યાદિત યોગ્ય વિકલ્પ પસંદ કરો. આરોગ્ય/આધાર માહિતી જાહેર ન કરો.
7. Deploy થયા પછી મળતી URL `https://script.google.com/macros/s/.../exec` નકલ કરો.

## APK બનાવવા
1. Android Studio માં આ ફોલ્ડર ખોલો.
2. Gradle sync પૂર્ણ થવા દો.
3. Build → Build APK(s) પસંદ કરો.
4. APK સામાન્ય રીતે `app/build/outputs/apk/debug/app-debug.apk` માં મળશે.
5. APK ખોલો; પહેલી વાર મળેલી Web App URL દાખલ કરો.

## નોંધ
- આ સ્રોત પ્રોજેક્ટ છે, તૈયાર/સહી કરેલી APK નથી.
- અહીં Android SDK/Gradle build environment ઉપલબ્ધ ન હોવાથી APK compile કરી શકાઈ નથી.
- Web App URL વગર એપને વાસ્તવિક Google Sheet સાથે જોડીને ચકાસી શકાતી નથી.
- Google Apps Script ના access permissions યોગ્ય રીતે ગોઠવો; આરોગ્ય અને ઓળખની વિગતો સંવેદનશીલ છે.
