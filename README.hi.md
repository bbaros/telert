
# टेलर्ट – आपके टर्मिनल के लिए अलर्ट

[English](README.md) | [हिन्दी](README.hi.md) | [中文 (简体)](README.zh-CN.md) | [Español](README.es.md)

<p align="center">
  <img src="https://github.com/navig-me/telert/raw/main/telert.png" alt="telert logo" width="150">
</p>

**संस्करण 0.1.41**

[![GitHub Stars](https://img.shields.io/github/stars/navig-me/telert?style=social)](https://github.com/navig-me/telert/stargazers)
[![PyPI version](https://img.shields.io/pypi/v/telert)](https://pypi.org/project/telert/)
[![Downloads](https://static.pepy.tech/personalized-badge/telert?period=month&units=international_system&left_color=grey&right_color=blue&left_text=downloads)](https://pepy.tech/project/telert)
[![License](https://img.shields.io/github/license/navig-me/telert)](https://github.com/navig-me/telert/blob/main/docs/LICENSE)
[![Marketplace](https://img.shields.io/badge/GitHub%20Marketplace-Use%20this%20Action-blue?logo=github)](https://github.com/marketplace/actions/telert-run)
[![VS Code Marketplace](https://vsmarketplacebadges.dev/version/Navig.telert-vscode.svg?subject=VS%20Code%20Marketplace&style=flat-square)](https://marketplace.visualstudio.com/items?itemName=Navig.telert-vscode)

## 📱 अवलोकन

टेलर्ट एक हल्का टूल है जो आपके टर्मिनल कमांड या पायथन कोड समाप्त होने पर नोटिफिकेशन भेजता है। यह कई नोटिफिकेशन चैनल्स को सपोर्ट करता है:

- **मैसेजिंग ऐप्स**: टेलीग्राम, माइक्रोसॉफ्ट टीम्स, स्लैक, डिस्कॉर्ड
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

## 🤝 योगदान / लाइसेंस

PRs और सुझावों का स्वागत है!  
MIT लाइसेंस के अंतर्गत लाइसेंस प्राप्त – `LICENSE` फ़ाइल देखें।

## 👏 आभार

इस प्रोजेक्ट को उन सभी योगदानकर्ताओं के सुझावों और फीडबैक से बेहतर बनाया गया है। यदि यह टूल आपके लिए उपयोगी है, तो कृपया [Buy Me a Coffee](https://www.buymeacoffee.com/mihirk) पर सपोर्ट करने पर विचार करें ☕

### अपनी परियोजनाओं के लिए VPS चाहिए?

इन प्रदाताओं को आज़माएं:

- [Vultr](https://www.vultr.com/?ref=9752934-9J) — $100 फ्री क्रेडिट
- [DigitalOcean](https://m.do.co/c/cdf2b5a182f2) — $200 फ्री क्रेडिट
