# 📊 Gold Spread Bot

A Telegram bot for real-time monitoring of the price spread between **PAXG** (Paradex) and **XAUT** (MEXC) — two gold-backed crypto tokens traded on different exchanges.

![Bot Preview](pic.jpg)

---

## 💡 What It Does

The bot tracks live prices of gold-pegged tokens across two exchanges and calculates the spread between them — useful for arbitrage monitoring and market analysis.

- **PAXG-USD-PERP** — fetched from [Paradex](https://paradex.trade) via WebSocket (real-time order book)
- **XAUT_USDT** — fetched from [MEXC](https://www.mexc.com) via REST API

The bot displays:
- Live mid-price from each exchange
- Absolute spread in USD
- Relative spread in %

Updates every **10 seconds** directly in the Telegram message.

---

## 🚀 How to Use

1. Find the bot on Telegram and send `/start`
2. Press **Start Tracking**
3. Watch live prices update every 10 seconds
4. Press **Stop** to pause tracking

---

## How to Run

### Option 1 — GitHub Actions (quick demo, free)

1. Fork this repository
2. Go to **Settings → Secrets and variables → Actions**
3. Add a secret: `BOT_TOKEN` = your Telegram bot token (get it from [@BotFather](https://t.me/BotFather))
4. Go to **Actions → Run Telegram Bot → Run workflow**

GitHub Actions free tier provides 2,000 minutes/month. Each run lasts up to 6 hours.

---

### Option 2 — VPS Server (recommended for 24/7)

For continuous operation, deploy on a Linux VPS (e.g. Hetzner, DigitalOcean, around $4-6/month).

**Step 1 — Connect to your server:**

    ssh root@your_server_ip

**Step 2 — Clone the repository:**

    git clone https://github.com/natalialeaiart/gold-spread-bot.git
    cd gold-spread-bot

**Step 3 — Install dependencies:**

    pip install -r requirements.txt

**Step 4 — Create .env file with your token:**

    echo "BOT_TOKEN=your_token_here" > .env

**Step 5 — Run with auto-restart:**

    screen -S bot
    python bot.py

The bot will run 24/7 and restart automatically if the server reboots.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.11 | Core language |
| python-telegram-bot | Telegram Bot API |
| websockets | Real-time Paradex data |
| aiohttp | MEXC REST API calls |
| asyncio | Async concurrent execution |
| python-dotenv | Secure token management |
| GitHub Actions | CI/CD and scheduled runs |

---

## Project Structure

    gold-spread-bot/
    ├── bot.py                    # Main bot code
    ├── requirements.txt          # Python dependencies
    ├── .env                      # Your secret token (not committed)
    ├── .gitignore                # Excludes .env and venv
    └── .github/
        └── workflows/
            └── run_bot.yml       # GitHub Actions workflow

---

## Security Notes

- Never commit your `.env` file — it contains your bot token
- Use GitHub Secrets for CI/CD deployments
- Keep your repository private if sharing with clients

---

## Author

**Natalia** — freelance developer specializing in trading bots, automation, and crypto tools.

GitHub: [@natalialeaiart](https://github.com/natalialeaiart)

---

## License

MIT — free to use and modify with attribution.
