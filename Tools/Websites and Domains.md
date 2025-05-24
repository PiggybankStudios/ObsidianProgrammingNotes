- [ ] You can run `dig` in Linux to check DNS entries (helpful when waiting for a change to take affect)
	- Example: `dig _github-pages-challenge-USERNAME.WEBSITE.com +nostats +nocomments +nocmd TXT`
- [ ] Github routing for a domain requires
      **`A` entries:**
	- Address: `185.199.108.153` TTL: `7207`
	- Address: `185.199.109.153` TTL: `7207`
	- Address: `185.199.110.153` TTL: `7207`
	- Address: `185.199.111.153` TTL: `7207`
	  **`CNAME` entry:**
	- HOSTNAME: `www` Address: `USERNAME.github.io` TTL: `7207`
	  **`TXT` entry:**
	- HOSTNAME: `_github-pages-challenge-USERNAME` Address: `[Copy from Github]`
- [ ] Github pages urls take the form: `USERNAME.github.io/REPO_NAME/` (trailing forward slash is required!)
- [ ] An apex domain is a custom domain that does not contain a subdomain, such as `example.com`. Apex domains are also known as base, bare, naked, root apex, or zone apex domains.
- [ ] 