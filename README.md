
# EoxStats 🚀

EoxStats is a high-performance, fully asynchronous, Folia-compatible statistics tracking plugin designed for large Minecraft networks (5000+ players). It completely replaces the server-crashing Vanilla JSON stat system and safely stores player data into a MySQL/MariaDB database using HikariCP.

## 🌟 Features
* **Zero TPS Impact:** All database read/write operations and leaderboard calculations are handled asynchronously on background threads.
* **Folia Support:** Specifically engineered to comply with Folia's strict regional threading models.
* **Clean Data:** Tracks only what matters for PvP servers: **Kills, Deaths, and Playtime**. No bloat, no tracked pig kills or walked blocks.
* **In-Memory Caching:** Top 10 leaderboards are cached in memory and updated every 10 minutes. 5,000 players can view the hologram leaderboards simultaneously without a single database query.
* **PlaceholderAPI Integration:** Ready to use with Holograms, Scoreboards, and TAB plugins.

---

## 📦 Installation
1. Disable Vanilla Minecraft stats saving in `spigot.yml` to prevent lag and corruption crashes:
   ```yaml
   stats:
     disable-saving: true
   ```
2. Drop `EoxStats.jar` into your `plugins` folder.
3. Start the server to generate the `config.yml`.
4. Configure your MySQL/MariaDB credentials in `plugins/EoxStats/config.yml`.
5. Restart the server.

---

## ⚙️ Configuration (`config.yml`)
```yaml
database:
  host: "localhost"
  port: 3306
  name: "minecraft"
  username: "root"
  password: "yourpassword"
  useSSL: false
```

---

## 🏆 PlaceholderAPI Variables

### 👤 Personal Stats
* `%eoxstats_kills%` - Total kills
* `%eoxstats_deaths%` - Total deaths
* `%eoxstats_kd%` - Kill/Death Ratio (e.g. 1.50)
* `%eoxstats_playtime%` - Formatted Playtime (e.g. `1g 2s 30d`)

### 🥇 Leaderboards (Top 10)
Replace `1` with any rank from `1` to `10`.

**Top Kills:**
* `%eoxstats_top_kills_name_1%`
* `%eoxstats_top_kills_value_1%`

**Top Deaths:**
* `%eoxstats_top_deaths_name_1%`
* `%eoxstats_top_deaths_value_1%`

**Top Playtime:**
* `%eoxstats_top_playtime_name_1%`
* `%eoxstats_top_playtime_value_1%`

---

## 🛠️ Built With
* Java 17+
* Bukkit / Paper API (Folia Supported)
* HikariCP (Database Connection Pooling)
* PlaceholderAPI
```
