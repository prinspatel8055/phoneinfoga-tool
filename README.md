# PhoneInfoga v2.11.0 - Advanced OSINT Phone Number Investigation Tool

<p align="center">
  <img src="./docs/images/banner.png" width="500" alt="PhoneInfoga Logo"/>
</p>

<p align="center">
  <b>Information Gathering & OSINT Reconnaissance Framework for International Phone Numbers</b>
</p>

---

## 📌 પરિચય (Overview)

**PhoneInfoga** એ આંતરરાષ્ટ્રીય (International) ફોન નંબરો વિશે સાર્વજનિક રૂપે ઉપલબ્ધ (OSINT - Open Source Intelligence) માહિતી એકત્રિત કરવા માટેનું એક અદ્યતન ટૂલ છે. આ ટૂલ Go (Golang) ભાષામાં લખાયેલું છે.

તે નંબરનું ફોર્મેટ, દેશ, કેરિયર (ઓપરેટર), લાઇનનો પ્રકાર (Mobile, Landline, VoIP) અને ઇન્ટરનેટ પર રહેલી પબ્લિક ફૂટપ્રિન્ટ્સ (Google Search Dorks) સ્કેન કરે છે.

---

## 🚀 પ્રોજેક્ટ કેવી રીતે રન કરવો? (Quick Start Guide)

આ પ્રોજેક્ટમાં `bin/phoneinfoga.exe` પહેલેથી જ તૈયાર છે. તેને ૨ રીતે રન કરી શકાય છે:

### રીત ૧: ગ્રાફિકલ વેબ UI મોડ (Web Dashboard - ભલામણ કરેલ)

1. ટર્મિનલ / PowerShell ખોલો અને નીચેનો કમાન્ડ ચલાવો:
   ```powershell
   .\bin\phoneinfoga.exe serve -p 5050
   ```
   *(નોંધ: જો પોર્ટ 5000 પહેલેથી વપરાશમાં હોય, તો `-p 5050` વાપરીને સરળતાથી ચાલુ કરી શકાય છે).*

2. તમારા બ્રાઉઝરમાં નીચેનું સરનામું ખોલો:
   👉 **[http://localhost:5050](http://localhost:5050)**

3. સ્ક્રીન પર નંબર (જેમ કે `+916351160293`) નાખીને **Scan** બટન પર ક્લિક કરો.

---

### રીત ૨: કમાન્ડ લાઇન (CLI) મોડ

જો તમારે બ્રાઉઝર વગર સીધું જ ટર્મિનલમાંથી સ્કેન કરવું હોય:

```powershell
.\bin\phoneinfoga.exe scan -n "+91XXXXXXXXXX"
```

ઉદાહરણ તરીકે:
```powershell
.\bin\phoneinfoga.exe scan -n "+916351160293"
```

---

## 🔍 પરિણામોમાં "No Results Found" શા માટે આવે છે? (Understanding OSINT vs Truecaller)

ઘણીવાર ગૂગલ સર્ચની લિંક ખોલતાં **"No results found for site:facebook.com..."** એવું દેખાય છે. આનો અર્થ એ **નથી** કે ટૂલ બગડેલું છે. આનું વાસ્તવિક કારણ:

1. **નંબર પ્રાઇવેટ (ખાનગી) છે:** જો કોઈ વ્યક્તિએ પોતાનો નંબર ફેસબુક, ઇન્સ્ટાગ્રામ કે અન્ય કોઈ વેબસાઇટ પર પબ્લિકલી પોસ્ટ ન કર્યો હોય, તો ગૂગલ પાસે તેનો કોઈ રેકોર્ડ હોતો નથી.
2. **સોશિયલ મીડિયા પ્રાઇવસી:** Facebook અને Instagram હવે પ્રાઇવસી પોલિસી હેઠળ યુઝર્સના ફોન નંબરો ગૂગલ સર્ચમાં આવવા દેતા નથી.
3. **Truecaller થી અલગ કાર્યપદ્ધતિ:**
   * **Truecaller:** લોકોના ફોનમાંથી એડ્રેસ બુક (સંપર્કો) સિંક કરીને પોતાનો પ્રાઇવેટ ડેટાબેઝ બનાવે છે, જેથી સામાન્ય લોકોના નામ પણ દેખાઈ જાય છે.
   * **PhoneInfoga:** કોઈનો પ્રાઇવેટ ડેટા ચોરતું નથી; તે માત્ર ઓપન વેબ (લીગલ OSINT) પર ઉપલબ્ધ ડેટા જ શોધે છે.

| લક્ષણ (Feature) | PhoneInfoga (OSINT) | Truecaller |
| :--- | :--- | :--- |
| **ડેટા સ્ત્રોત** | ગૂગલ, પબ્લિક વેબસાઇટ્સ અને ઓપન APIs | યુઝર્સની એડ્રેસ બુકનો પ્રાઇવેટ ડેટા |
| **સામાન્ય વ્યક્તિનું નામ** | ના મળે (જો ઇન્ટરનેટ પર પબ્લિક ન હોય) | મળી જાય છે |
| **પ્રાઇવસી સુરક્ષા** | ૧૦૦% સુરક્ષિત (માત્ર પબ્લિક ડેટા) | પર્સનલ કોન્ટેક્ટ લિસ્ટ લીક કરે છે |
| **મુખ્ય ઉપયોગ** | સાયબર ક્રાઈમ ઇન્વેસ્ટિગેશન, ફ્રોડ/સ્કેમર તપાસ | સામાન્ય કોલર આઈડી |

---

## ⚙️ ઉપલબ્ધ સ્કેનર્સ (Scanners)

* **`local`**: ઓફલાઇન લાઇબ્રેરી દ્વારા દેશ, માન્યતા, નંબર ફોર્મેટ અને કેરિયરની વિગતો આપે છે.
* **`googlesearch`**: સોશિયલ મીડિયા, સ્કેમ ડિરેક્ટરી અને લીક્સ ચેક કરવા માટે Google Dorks લિંક્સ બનાવે છે.
* **`numverify`**: Numverify API દ્વારા કેરિયર અને લોકેશન ડેટા લાવે છે (API Key જરૂરી).
* **`googlecse`**: Google Custom Search Engine દ્વારા પ્રોગ્રામેટિક વેબ સર્ચ કરે છે (API Key જરૂરી).
* **`ovh`**: ટેલિકોમ પ્રોવાઇડર ડેટાબેઝ ચેક કરે છે.

---

## 📁 .gitignore અંગે મહત્વની માહિતી (GitHub Upload Notes)

આ રીપોઝીટરીની `.gitignore` ફાઇલમાં નીચે મુજબની એન્ટ્રીઓ છે:
```gitignore
# Binaries for programs and plugins
*.exe
*.exe~
*.dll
*.so
*.dylib
/bin
```

⚠️ **ધ્યાનમાં રાખવા જેવી બાબત:** 
* `.gitignore` માં `/bin` અને `*.exe` હોવાને કારણે `bin/phoneinfoga.exe` ફાઇલ ગીટહબ પર ડિફોલ્ટ રીતે પુશ નહીં થાય.
* જો તમે ઈચ્છો કે બીજા લોકો સીધી જ `.exe` ફાઇલ ડાઉનલોડ કરીને વાપરી શકે, તો કાં તો `.gitignore` માંથી `/bin` હટાવવું પડે અથવા `git add -f bin/phoneinfoga.exe` કમાન્ડ વાપરવો પડે.

---

## 📄 વધારાના દસ્તાવેજો (Documentation Files)

આ ફોલ્ડરમાં યુઝર્સની સરળતા માટે સંપૂર્ણ ગાઈડ તૈયાર કરીને મૂકેલી છે:
* 📘 **Word Document:** [`PhoneInfoga_User_Guide.docx`](./PhoneInfoga_User_Guide.docx)
* 📕 **PDF Document:** [`PhoneInfoga_User_Guide.pdf`](./PhoneInfoga_User_Guide.pdf)

---

## ⚖️ લાઇસન્સ (License)

આ પ્રોજેક્ટ **GNU General Public License v3.0** હેઠળ લાઇસન્સ થયેલ છે.
