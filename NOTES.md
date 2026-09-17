# Hall's Plumbing, LLC — preview site

Static site. No build step. `index.html` + `styles.css` + `assets/`.

## Brand

Colours sampled straight out of Jerry's logo (`assets-src/gphoto-1.jpg`, the
shirt photo from his Google listing). Jerry confirmed navy + silver.

| Token | Hex | Where it came from |
|---|---|---|
| navy | `#131A2B` | logo background |
| silver | `#C3C2C4` | logo lettering |
| sky | `#91BDEA` | the speed-bar under the logo — accent only |

`assets/logo.png` is the wordmark cut out of that photo onto transparency. It
only sits on navy. If Jerry has the original vector file, swap it in.

## Where every factual claim on the page came from

| Claim on the page | Source | Solid? |
|---|---|---|
| (434) 429-3005 | Jerry's own van lettering + every listing | yes |
| hallsplumbingva@gmail.com | Jerry's own van lettering | yes |
| 508 Cliff St, Danville VA 24540 | VA business registry | yes, but see below |
| 4.5 stars / 88 Google reviews | Google Business Profile, 17 Sep 2026 | yes, will drift |
| A+ BBB rating | BBB profile | re-check at launch |
| Open 24 hours | Google Business Profile | confirm with Jerry |
| Licensed · Bonded · Insured | Jerry's own van lettering | yes |
| "30+ years in the trade" | Jerry's own copy on listing sites | confirm with Jerry |
| "Licensed LLC since August 2013" | VA registry, reg. date 8/17/2013 | yes |

## Open questions for Jerry

- [ ] **Founding year.** 2013 is only the date the LLC paperwork was filed. Josh
      recalls Jerry's father was plumbing before Jerry was born. Get the real
      year — it is a much stronger story. See the TODO in the About section.
- [ ] Service-area town lists (VA + NC) — drafted off the map, he should prune
- [ ] "Free estimates" and "usually the same day" — his promises to make, not ours
- [ ] Is 508 Cliff St his home address? If so, maybe keep it off the page
- [ ] Delete the `.preview-note` div in `index.html` before going live

## The domain situation

His Google Business Profile "Website" button currently points at
`http://www.hallsplumbingllc.com/` — a squatter's parked lead-gen page that
routes callers to Roto-Rooter. Registered 13 Jan 2026, listed on GoDaddy at
~$164. Repointing the Google listing is free and lands faster than the purchase.
