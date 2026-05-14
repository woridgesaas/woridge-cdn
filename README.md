# Woridge CDN

Lightweight HTTP cache for static assets (avatars, images, PDFs) using Nginx + MinIO.

## How it works
Angular → Kong → Nginx (cache) → MinIO (public bucket)

↑

Disk / RAM cache
### 1. MinIO bucket must be public

The CDN accesses MinIO directly without authentication. Make your bucket public:

```bash
mc anonymous set download local/avatars

```

### 2. Cache settings
| Parameter | Value |
|-----------|-------|
| Cache location | `/var/cache/nginx` (disk) |
| Max size | 5GB |
| Cache duration (200 OK) | 7 days |
| Cache duration (404) | 1 minute |
| Inactivity cleanup | 30 days |