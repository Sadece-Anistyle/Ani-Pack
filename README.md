# @here @everyone bu paket adım anistyle iken yapilmistir. Suan adimiz klaze

Discord botunuz için dinamik ve esnek aktivite sistemi. Belirli aralıklarla otomatik olarak değişen bot aktiviteleri oluşturun ve webhook entegrasyonuyla aktivite değişimlerini takip edin.

[![npm version](https://img.shields.io/npm/v/anipack)](https://www.npmjs.com/package/anipack)
[![npm downloads](https://img.shields.io/npm/dt/anipack)](https://www.npmjs.com/package/anipack)
[![License](https://img.shields.io/npm/l/anipack)](https://github.com/hasbutcu/anipack/blob/main/LICENSE)

## 📦 Kurulum

```bash
npm install anipack (anipack olmassa npm i ani)
```

## 🚀 Özellikler

- 🔄 Otomatik değişen bot aktiviteleri
- 🎮 Farklı aktivite türleri (Oynuyor, İzliyor, Dinliyor, Yayında, vb.)
- ⏱️ Özelleştirilebilir zaman aralıkları
- 📊 Discord Webhook entegrasyonu
- 🛠️ Kolay konfigürasyon ve kurulum

## 📚 Kullanım

### Temel Kullanım

```javascript
const { Client, GatewayIntentBits } = require('discord.js');
const { ani, anipack } = require('anipack');

const client = new Client({
  intents: [GatewayIntentBits.Guilds]
});

client.on('ready', () => {
  console.log(`${client.user.tag} ile giriş yapıldı!`);
  
  ani(client);
});

client.login('TOKEN');
```

### Webhook ile Kullanım

```javascript
const { Client, GatewayIntentBits } = require('discord.js');
const { ani } = require('anipack');

const client = new Client({
  intents: [GatewayIntentBits.Guilds]
});

client.on('ready', () => {
  console.log(`${client.user.tag} ile giriş yapıldı!`);
  
  const webhook = "https://discord.com/api/webhooks/your-webhook-url";
  ani(client, webhook);
});

client.login('TOKEN');
```

### Config Dosyası ile Kullanım

```javascript
const { Client, GatewayIntentBits } = require('discord.js');
const { ani } = require('anipack');
const config = require('./config.json'); // { "webhook": "https://..." }

const client = new Client({
  intents: [GatewayIntentBits.Guilds]
});

client.on('ready', () => {
  console.log(`${client.user.tag} ile giriş yapıldı!`);
  
  ani(client, config);
});

client.login('TOKEN');
```

### Özel Aktiviteler ile Kullanım

```javascript
const { Client, GatewayIntentBits } = require('discord.js');
const { anipack } = require('anipack');

const client = new Client({
  intents: [GatewayIntentBits.Guilds]
});

client.on('ready', () => {
  console.log(`${client.user.tag} ile giriş yapıldı!`);
  
  const activities = [
    { name: 'Müzik', type: 'listening', status: 'online' },
    { name: 'Minecraft', type: 'playing', status: 'idle' },
    { name: 'YouTube', type: 'watching', status: 'dnd' },
    { name: 'Twitch Yayını', type: 'streaming', url: 'https://twitch.tv/anistyle', status: 'online' }
  ];
  
  anipack(client, activities, 60000, true, config.webhook);
});

client.login('TOKEN');
```

## 📋 Fonksiyon Referansları

### `ani(client, webhook)`

Basit ve hızlı bir şekilde botunuza değişen aktiviteler ekler. Her 15 saniyede bir farklı bir aktivite ayarlar ve bot durumunu her zaman "idle" olarak ayarlar.

| Parametre | Tip | Açıklama | Varsayılan |
|-----------|-----|----------|------------|
| client | Object | Discord.js client nesnesi | (Zorunlu) |
| webhook | String veya Object | Discord webhook URL'si veya webhook bilgisini içeren obje | null |

### `anipack(client, activities, interval, logActivity, webhook)`

Daha gelişmiş özelleştirme sağlayan ve özel aktiviteler belirlemenize olanak tanıyan fonksiyon.

| Parametre | Tip | Açıklama | Varsayılan |
|-----------|-----|----------|------------|
| client | Object | Discord.js client nesnesi | (Zorunlu) |
| activities | Array | Aktivite bilgilerini içeren dizi | (Zorunlu) |
| interval | Number | Aktivite değişim süresi (ms) | 120000 (2 dakika) |
| logActivity | Boolean | Aktivite değişimlerini konsola yazdırma | true |
| webhook | String veya Object | Discord webhook URL'si veya webhook bilgisini içeren obje | null |

## 📝 Aktivite Yapısı

Aktivite nesnesi aşağıdaki özelliklere sahip olabilir:

```javascript
{
  name: 'Ani Pack',
  type: 'playing',      
  url: 'https://discord.gg/deus',   
  status: 'online'     
}
```
## 🔔 Webhook Bildirimleri

Webhook özelliği etkinleştirildiğinde, her aktivite değişiminde aşağıdaki bilgileri içeren bir embed mesajı webhook'a gönderilir:

- Aktivite İsmi
- Aktivite Türü
- Bot Durumu
- URL (eğer varsa)
- Zaman damgası

## 📃 Örnek config.json

```json
{
  "token": "your-discord-bot-token",
  "webhook": "https://discord.com/api/webhooks/your-webhook-url",
  "prefix": "!",
  "botSettings": {
    "activityInterval": 60000
  }
}
```

## 📄 Lisans

Bu proje [MIT Lisansı](LICENSE) altında lisanslanmıştır.

## 👨‍💻 Geliştirici

ani tarafından geliştirilmiştir.

- Discord: @anistyle.html
- GitHub: [github.com/anidesign](https://github.com/Sadece-Anistyle)
- Website: [ani.com](https://ani.com)

---

🌟 anipack'i beğendiyseniz yıldız vermeyi unutmayın! 🌟
