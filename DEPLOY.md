# Deploy

A production deploy scriptje és a teljes dokumentáció a frontend repóban van (ugyanazon a gépen, testvér mappa):

```
..\Életkert_v2.0\scripts\deploy.ps1 -Target backend
```

Részletek: [Életkert_v2.0\DEPLOY.md](../../Életkert_v2.0/DEPLOY.md) és
[Életkert_v2.0\AGENTS.md](../../Életkert_v2.0/AGENTS.md).

**Build előtt ellenőrizd, hogy a `npm run build` helyben sikeresen lefut.** A munkakönyvtár jelenleg
committálatlan, félbehagyott függőség-frissítést tartalmaz (`package.json`, `package-lock.json`, törölt
`vercel.json` – lásd a `repair2.0` commitot), és a `npm run build` emiatt hibával áll le
(`@strapi/plugin-cloud` 5.x nem kompatibilis a `@strapi/strapi` 4.25.x-szel). Ezt javítani kell (vagy vissza
kell állni egy tiszta, build-elhető állapotra), mielőtt a backend deploy célt futtatnád.

A szerveren ez a projekt a `/root/apps/eletkertadmin` mappából fut, PM2 `admin` folyamatként
(`pm2 restart admin`), a `strapi.eletkertjudittal.hu` nginx site mögött (`127.0.0.1:1337`).
