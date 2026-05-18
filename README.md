# Mugiwara Stream — APK Releases

Mirror CDN per le release APK dell'app Android TV **Mugiwara Stream**.

Tutte le release stabili e beta sono pubblicate qui come **GitHub Releases**, servite dal CDN globale di Microsoft Azure / Fastly. Questo repo serve come fallback automatico se il backend primario `backend.mugiwara.click` non risponde.

## Come l'app trova il file giusto

L'app fa polling al manifest pubblico:
```
GET https://backend.mugiwara.click/api/system/app-version
```

che ritorna:
```json
{
  "version_code": 63,
  "version_name": "0.6.3-beta",
  "apk_url": "https://backend.mugiwara.click/download/...",
  "apk_url_mirror": "https://github.com/Cyberbreach/mugiwara-stream-releases/releases/download/.../..."
}
```

Se `apk_url` (primary) timeout o ritorna body invalido, l'app passa automaticamente a `apk_url_mirror`.

## Per i tester

Vai su [Releases](https://github.com/Cyberbreach/mugiwara-stream-releases/releases) e scarica l'APK più recente.

Requisiti: Android TV 6.0+ (API 23), 80MB liberi.
