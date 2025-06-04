
# टेलर्ट – आपके टर्मिनल के लिए अलर्ट

[English](README.md) | [हिन्दी](README.hi.md) | [中文 (简体)](README.zh-CN.md) | [Español](README.es.md)

<p align="center">
  <img src="https://github.com/navig-me/telert/raw/main/telert.png" alt="telert logo" width="150">
</p>

**संस्करण 0.2.3**

[![GitHub Stars](https://img.shields.io/github/stars/navig-me/telert?style=social)](https://github.com/navig-me/telert/stargazers)
[![PyPI version](https://img.shields.io/pypi/v/telert)](https://pypi.org/project/telert/)
[![Downloads](https://static.pepy.tech/personalized-badge/telert?period=month&units=international_system&left_color=grey&right_color=blue&left_text=downloads)](https://pepy.tech/project/telert)
[![License](https://img.shields.io/github/license/navig-me/telert)](https://github.com/navig-me/telert/blob/main/docs/LICENSE)
[![Marketplace](https://img.shields.io/badge/GitHub%20Marketplace-Use%20this%20Action-blue?logo=github)](https://github.com/marketplace/actions/telert-run)
[![VS Code Marketplace](https://vsmarketplacebadges.dev/version/Navig.telert-vscode.svg?subject=VS%20Code%20Marketplace&style=flat-square)](https://marketplace.visualstudio.com/items?itemName=Navig.telert-vscode)

## 📱 अवलोकन

टेलर्ट एक हल्का टूल है जो आपके टर्मिनल कमांड या पायथन कोड समाप्त होने पर नोटिफिकेशन भेजता है। यह कई नोटिफिकेशन चैनल्स को सपोर्ट करता है:

- **मैसेजिंग ऐप्स**: टेलीग्राम, माइक्रोसॉफ्ट टीम्स, स्लैक, डिस्कॉर्ड
- **ईमेल**: ईमेल
- **मोबाइल डिवाइसेज़**: पुशओवर (Android और iOS)
- **लोकल नोटिफिकेशन**: डेस्कटॉप नोटिफिकेशन, ऑडियो अलर्ट
- **कस्टम इंटीग्रेशन**: HTTP एंडपॉइंट्स किसी भी सर्विस के लिए

यह लंबी चलने वाली प्रक्रियाओं, रिमोट सर्वर, CI पाइपलाइनों या महत्वपूर्ण कोड की निगरानी के लिए आदर्श है।

इसे CLI टूल, पायथन लाइब्रेरी, या नोटिफिकेशन API के रूप में उपयोग करें। टेलर्ट उपलब्ध है:
- एक पायथन पैकेज के रूप में: `pip install telert`
- एक डॉकर इमेज के रूप में: `docker pull ghcr.io/navig-me/telert:latest`
- क्लाउड-होस्टेड API के रूप में Replit, Railway, Render या Fly.io पर।

<img src="https://github.com/navig-me/telert/raw/main/docs/telert-demo.svg" alt="telert demo" width="600">

## 🚀 इंस्टॉलेशन और त्वरित शुरुआत

```bash
pip install telert
telert init
```

### मुख्य लाभ

- 📱 जब आपका कमांड समाप्त हो, तुरंत नोटिफिकेशन पाएं
- ⏱️ देखें कि कमांड या कोड को पूरा होने में कितना समय लगा
- 🚦 सफलता/असफलता की स्थिति और त्रुटि विवरण कैप्चर करें
- 📃 कमांड आउटपुट का अंश सीधे नोटिफिकेशन में देखें
- 🔄 शेल कमांड, पाइपलाइनों और पायथन कोड के साथ काम करता है


## 🚦 मॉनिटरिंग

### प्रोसेस मॉनिटरिंग

प्रोसेस संसाधन उपयोग की निगरानी करें और सीमा से अधिक होने पर सूचनाएं प्राप्त करें:

```bash
# प्रोसेस मेमोरी उपयोग की निगरानी
telert monitor process --command-pattern "ps aux | grep मेरी_ऐप" --memory-threshold 2G

# एकाधिक प्रोसेस की निगरानी
telert monitor process --command-pattern "ps aux | grep -E 'nginx|postgres'" --cpu-threshold 80

# सभी प्रोसेस मॉनिटर सूचीबद्ध करें
telert monitor process --list

# प्रोसेस मॉनिटरिंग बंद करें
telert monitor process --stop <मॉनिटर-आईडी>
```

### लॉग फाइल मॉनिटरिंग

लॉग फाइलों में विशेष पैटर्न के लिए नजर रखें और मिलान मिलने पर संदर्भ के साथ सूचनाएं प्राप्त करें:

```bash
# पैटर्न के लिए लॉग फाइल की निगरानी
telert monitor log --file "/var/log/ऐप्लिकेशन.log" --pattern "त्रुटि|गंभीर" --provider telegram

# संदर्भ के साथ उन्नत निगरानी
telert monitor log \
  --file "/var/log/nginx/error.log" \
  --pattern ".*\\[error\\].*" \
  --context-lines 5 \
  --cooldown 300 \
  --provider slack

# सभी लॉग मॉनिटर सूचीबद्ध करें
telert monitor log --list
```

### नेटवर्क मॉनिटरिंग

विभिन्न जांच प्रकारों के साथ नेटवर्क कनेक्टिविटी और सेवाओं की निगरानी करें:

```bash
# बेसिक पिंग मॉनिटरिंग
telert monitor network --host उदाहरण.com --type ping --interval 60 --provider slack

# HTTP एंडपॉइंट मॉनिटरिंग
telert monitor network \
  --url https://api.उदाहरण.com/health \
  --expected-status 200 \
  --timeout 5 \
  --provider telegram

# TCP पोर्ट मॉनिटरिंग
telert monitor network --host db.उदाहरण.com --port 5432 --provider email

# सभी नेटवर्क मॉनिटर सूचीबद्ध करें
telert monitor network --list
```

मॉनिटरिंग सुविधाओं के बारे में विस्तृत जानकारी के लिए [मॉनिटरिंग गाइड](https://github.com/navig-me/telert/blob/main/docs/MONITORING.md) देखें।

## 🤝 योगदान / लाइसेंस

PRs और सुझावों का स्वागत है!  
MIT लाइसेंस के अंतर्गत लाइसेंस प्राप्त – `LICENSE` फ़ाइल देखें।

इस प्रोजेक्ट को उन सभी योगदानकर्ताओं के सुझावों और फीडबैक से बेहतर बनाया गया है। यदि यह टूल आपके लिए उपयोगी है, तो कृपया [Buy Me a Coffee](https://www.buymeacoffee.com/mihirk) पर सपोर्ट करने पर विचार करें ☕

### अपनी परियोजनाओं के लिए VPS चाहिए?

इन प्रदाताओं को आज़माएं:

- [Vultr](https://www.vultr.com/?ref=9752934-9J) — $100 फ्री क्रेडिट
- [DigitalOcean](https://m.do.co/c/cdf2b5a182f2) — $200 फ्री क्रेडिट
