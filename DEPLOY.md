# Deploy FitTrack

Connect **DevMiguelSilva/fittrack** to the existing Vercel project **fit-tracker**. Leave Root Directory empty and retain production branch `main`, current domains, environment scopes, and other project settings.

`vercel.json` supplies Vite, `npm run build`, output `dist`, and the SPA deep-link rewrite. Run `npm ci`, `npm run dev`, `npm run build`, and `npm run lint` from repository root. Local development uses port 5175.

## Configuration and data

Preserve local `.env` and `.env.local`; they are ignored by Git. `.env.example` lists `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`. Keep the existing values and scopes in Vercel and the same Supabase project. The split requires no database changes; retain `supabase/schema.sql` for future schema work.

Keep authentication, database tables, and the `fittrack-v1` browser storage key unchanged. Local browser records are bound to the existing origin, so preserve production domains.

## Release and rollback

Production custom address: `https://fittrack.miguelcode.dev`. Attach it to this existing Vercel project's Production environment. Cloudflare manages DNS only: use the exact CNAME Vercel recommends, DNS only, automatic TTL. Preserve Cloudflare nameservers and unrelated records; Vercel serves the app and HTTPS.

The existing Supabase project's Site URL is `https://fittrack.miguelcode.dev`. Allow the exact root return URL `https://fittrack.miguelcode.dev/` and retain existing local, preview, and Vercel return URLs. Current password sign-in and sign-up use the default client flow; there is no separate callback route. Email confirmation uses the configured Site URL when no redirect option is supplied. Keep Supabase service URLs, keys, database data, and schemas unchanged.

Supabase environment variables remain Production-only. A local-mode preview must not be promoted as the final cloud-enabled production build. Users sign in again on the custom address to access cloud records. Browser-only records and sessions are origin-bound; keep the old address usable without forced redirects or automatic storage transfer.

Verify a branch preview before production: deep-link refresh, sign-in, existing cloud records, routines, sessions, and weekly weight. Keep the previous production deployment for Vercel rollback. Existing domain: `fit-tracker-jet-ten.vercel.app`.

Relevant app history is preserved here; the original repository remains `DevMiguelSilva/portfolio-monorepo-archive`.
