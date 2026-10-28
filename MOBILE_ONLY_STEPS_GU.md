# Family Health Survey — માત્ર Android મોબાઇલથી APK મેળવવાની માર્ગદર્શિકા

આ પ્રોજેક્ટ Android APK ને GitHub Actions ના ક્લાઉડ બિલ્ડર પર બનાવે છે. અહીંથી તમારા Google/GitHub ખાતામાં સાઇન-ઇન, Sheet પરવાનગી મંજૂર કરવી કે વેબ એપ deploy કરવી શક્ય નથી; તે પગલાં તમે તમારા મોબાઇલ પર કરો.

## ભાગ 1 — Google Sheets જોડાણ તૈયાર કરો

**મહત્વપૂર્ણ:** પહેલાં મૂળ Google Sheet નો બેકઅપ બનાવો. આરોગ્ય, આધાર અને કુટુંબની વિગતો જાહેર ન કરો.

1. Chrome માં તમારી Google Sheet ખોલો. જરૂર પડે તો Chrome ના ત્રણ ડોટ મેનૂમાંથી **Desktop site** ચાલુ કરો.
2. Sheet માં **Extensions → Apps Script** ખોલો. જો આ તમારી હાલની Script project છે, તો પહેલા હાલના કોડનો બેકઅપ રાખો.
3. આ પ્રોજેક્ટની `apps-script-source/Code.gs` ફાઇલનો કોડ Apps Script ના `Code.gs` માં મૂકો.
4. `Index.html` નામની HTML ફાઇલ બનાવો અને `apps-script-source/Index.html` નો કોડ તેમાં મૂકો.
5. Save કરો. ફંક્શન પસંદગીમાંથી `setupSheet` પસંદ કરીને **Run** કરો અને Google ની પરવાનગી જાતે મંજૂર કરો. કોઈ error આવે તો આગળ વધતા પહેલાં તેને ઉકેલો; મૂળ ડેટા ડિલીટ ન કરો.
6. **Deploy → New deployment → Web app** પસંદ કરો. **Execute as** માં `Me` પસંદ કરો. **Who has access** માટે તમારી સંસ્થા મંજૂર કરે તે સૌથી મર્યાદિત વિકલ્પ પસંદ કરો. જાહેર access ન પસંદ કરો જો તે જરૂરી અને મંજૂર ન હોય.
7. Deploy થયા પછી મળતી `https://script.google.com/macros/s/.../exec` URL કૉપી રાખો. આ URL એપમાં પહેલી વાર દાખલ કરવી પડશે.

જો તમારી પાસે હજી Google Sheet જ ન હોય, તો પહેલાં નવી Google Sheet બનાવવી પડશે. આ ZIP ફાઇલમાં માત્ર Apps Script કોડ છે; તેમાં Google Sheet નો ડેટા/ID સામેલ નથી.

## ભાગ 2 — મોબાઇલથી APK ક્લાઉડમાં બિલ્ડ કરો

1. Chrome માં `https://github.com` ખોલો અને સાઇન ઇન કરો અથવા ખાતું બનાવો.
2. **New repository** બનાવી તેને **Private** રાખો.
3. આ ZIP ને મોબાઇલમાં extract કરો. GitHub પર ZIP ને ફક્ત એક ફાઇલ તરીકે અપલોડ ન કરો; અંદરની ફાઇલો/ફોલ્ડરો અપલોડ કરો. `.github/workflows/build-apk.yml` ફાઇલ પણ repository માં હોવી જરૂરી છે.
4. ફайલો `main` branch માં commit કરો. GitHub Actions ને મંજૂરી આપવાનું કહે તો સમીક્ષા કરીને મંજૂર કરો.
5. Repository માં **Actions → Build Family Health Survey APK → Run workflow** ખોલો.
6. Workflow લીલું થઈ પૂર્ણ થાય પછી તે run ખોલો. **Artifacts** વિભાગમાંથી `Family-Health-Survey-APK` ડાઉનલોડ કરો અને ZIP extract કરો. અંદર `app-debug.apk` મળશે.
7. APK પર ટૅપ કરીને ઇન્સ્ટોલ કરો. Android પૂછે તો ફક્ત તમે વિશ્વાસ કરતા browser/file manager માટે “Install unknown apps” મંજૂર કરો.
8. એપ ખોલીને ભાગ 1 માં મેળવેલી `/exec` URL દાખલ કરો.

## શું હજી ચકાસવાનું બાકી છે?

- આ ZIP Android Studio પ્રોજેક્ટ છે, તૈયાર APK નથી.
- APK compile થાય તે GitHub Actions ના સફળ build પર આધારિત છે.
- Google Apps Script Web App URL વગર Google Sheets સાથેનું જોડાણ ચકાસી શકાતું નથી.
- `Code.gs` ને હાલની Sheet સાથે જોડતાં પહેલાં header/ડેટા બદલાવની અસર સમજો અને બેકઅપ રાખો.
