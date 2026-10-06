# Deploy FitTrack

Connect **DevMiguelSilva/fittrack** to the existing Vercel project **fit-tracker**. Leave Root Directory empty and retain production branch `main`, current domains, environment scopes, and other project settings.

`vercel.json` supplies Vite, `npm run build`, output `dist`, and the SPA deep-link rewrite. Run `npm ci`, `npm run dev`, `npm run build`, and `npm run lint` from repository root. Local development uses port 5175.

## Configuration and data

Preserve local `.env` and `.env.local`; they are ignored by Git. `.env.example` lists `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`. Keep the existing values and scopes in Vercel and the same Supabase project. The split requires no database changes; retain `supabase/schema.sql` for future schema work.

Keep authentication, database tables, and the `fittrack-v1` browser storage key unchanged. Local browser records are bound to the existing origin, so preserve production domains.

## Release and rollback

Verify a branch preview before production: deep-link refresh, sign-in, existing cloud records, routines, sessions, and weekly weight. Keep the previous production deployment for Vercel rollback. Existing domain: `fit-tracker-jet-ten.vercel.app`.

Relevant app history is preserved here; the original repository remains `DevMiguelSilva/portfolio-monorepo-archive`.
