# ✅ DONE — went live 23 September 2026

**https://hallsplumbingllc.com** is live on Cloudflare Pages. The steps below
are kept as the record of how it was done, and for the next client site.

What actually happened differed from the plan in one way: hosting moved from
GitHub Pages to **Cloudflare Pages**, because GitHub's terms are a grey area
for a business site. See the  note.

**Still outstanding:** Jerry repointing his Google Business Profile Website box,
and his sign-off on the four advertising claims and the founding year.

---

# Go live on hallsplumbingllc.com

Everything below waits on one thing: **being added to Jerry's GoDaddy account.**
Nothing here can be done before that. Once you are in, this is about 15 minutes
of work plus waiting for DNS.

---

## Step 0 — before anything, check the site copy

These still need Jerry's word and they are on the live page right now:

- [ ] **The real founding year.** 2013 is only the LLC filing date. Josh says
      Jerry's father plumbed before Jerry was born. There is a `TODO` comment in
      the About section of `index.html` marking where the real story goes.
- [ ] **"30+ years in the trade"** — from his own listings, not confirmed by him.
- [ ] **"Free estimates"** and **"usually the same day"** — his promises to make.
- [ ] **A+ BBB rating** — true when checked; re-check on the day.
- [ ] **The VA / NC town lists** — drafted off the map. He should cross out
      anywhere he will not drive.
- [ ] **508 Cliff St.** It is NOT shown anywhere a visitor can read — the page
      says only "Danville, VA 24540". But it **is** in the structured data block
      at the top of `index.html`, which is what Google reads to match this site
      to his Business Profile. That address is already public on his Google
      listing and in the Virginia business registry, so this is not a new
      disclosure. If Jerry would rather it were gone entirely, delete the
      `streetAddress` line from the JSON-LD.
- [ ] **Delete the preview bar.** One line in `index.html`:
      `<div class="preview-note">…</div>`

---

## Step 1 — kill the fake page (do this first, on its own)

The domain is Jerry's but its nameservers still point at the previous owner's
Cloudflare account, so **the squatter's lead-gen page is still live and still
sends callers to Roto-Rooter.**

In GoDaddy: **Domain → DNS → Nameservers → change to GoDaddy's default.**

That one change alone takes the fake page down. Do it even if the website is not
ready. An empty page beats a page advertising a competitor.

Give it up to an hour, then check:

```
nslookup -type=NS hallsplumbingllc.com
curl -sI http://hallsplumbingllc.com/
```

You want the nameservers to stop saying `cloudflare.com`.

---

## Step 2 — point the domain at the site

In GoDaddy **DNS → Records**, delete any A/AAAA/CNAME records for `@` and `www`
that the previous owner left, then add:

**A records — host `@`** (all four):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**AAAA records — host `@`** (all four):

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**CNAME — host `www`** → `flopjunkie.github.io`
(just that — **no** repo name on the end)

> Verified against GitHub's own documentation on 22 Sep 2026. If this is being
> read much later, re-check the docs — GitHub has changed these IPs before.

---

## Step 3 — tell GitHub about the domain

Two ways, same result. Either add a file named `CNAME` at the repo root whose
only contents are:

```
hallsplumbingllc.com
```

…or set it in the repo under **Settings → Pages → Custom domain**.

**Do not do this before Step 2 has propagated.** GitHub verifies the DNS when
you set it, and if it cannot resolve it just sits in a failed state.

Then tick **Enforce HTTPS** once GitHub finishes issuing the certificate. That
usually takes a few minutes and can take up to an hour.

---

## Step 3a — swap the pre-launch URLs (easy to forget)

While the real domain still serves the squatter's page, `index.html` deliberately
points at the GitHub Pages address instead. Without that, texting the link would
pull a preview image off the fake site, and Google would be told the fake page
is the canonical one.

Once the domain is live, change all five back to `https://hallsplumbingllc.com/`:

- the `canonical` link
- `og:url`
- `og:image`
- `"url"` in the JSON-LD block
- `"image"` in the JSON-LD block

`robots.txt` and `sitemap.xml` already point at the real domain — leave them.

---

## Step 4 — check it properly

```
curl -sI https://hallsplumbingllc.com/        # expect 200
curl -sI https://www.hallsplumbingllc.com/    # expect a redirect to the apex
```

Then on a phone, not just a desktop: tap the call button, tap the text button,
and open the FAQ. Most of Jerry's visitors will be on a phone.

---

## Step 5 — the thing that actually makes the phone ring

**Jerry's Google Business Profile still has the squatter's address in the
Website box.** Until that is changed, Google keeps sending people to the wrong
place regardless of what this site does.

He edits it himself at **business.google.com** → his profile → Website →
`https://hallsplumbingllc.com`. Free, and it usually shows up within hours.

Also worth doing while he is in there: check the hours, and add photos of his
own work. Real photographs of finished jobs would lift this site more than any
other single change — there are none on it at the moment.

---

## Later, cheap, worth doing

- Real photographs of Jerry, his van and finished work, to replace the
  graphic-only treatment.
- Three real review quotes on the reviews band, once Jerry picks them.
- A one-tap "leave us a review" link he can text customers the day after a job.
