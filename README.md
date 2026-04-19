# Active-Footprinting
This lab involved basic reconnaissance on bulanbintanghq.com. I performed DNS lookup (IP: 172.67.68.161), WHOIS lookup (GoDaddy registrar), and technology fingerprinting (WordPress + WooCommerce). A login form was also discovered. The exercise demonstrates how attackers gather public information to identify potential vulnerabilities.

# Penetration Testing Steps

| Step | Tool | Finding | Interpretation | Mitigation |
|------|------|---------|----------------|-------------|
| 1 | Manual | bulanbintanghq.com – Malaysian clothing brand selling Baju Melayu & Baju Kurung | An attractive target for hackers is an e-commerce website that handles user logins and payments. | N/A (this is the chosen target) |
| 2 | nslookup + whois.domainntools.com | IP: 172.67.68.161<br>Registrar: GoDaddy.com, LLC<br>Name Servers: GREG.NS.CLOUDFLARE.COM | The website is hosted on a server in the United States (probably shared hosting). Shared hosting implies that other websites on the same server could be vulnerable if one is hacked. | To conceal your true IP address, use a dedicated server or cloud WAF (Cloudflare). |
| 3 | Wappalyzer Extension | CMS: WordPress<br>E-commerce: WooCommerce<br>Web Server: nginx/Apache<br>Tracking: Google Analytics, Facebook Pixel | The most compromised CMS combination is WordPress + WooCommerce. There may be known vulnerabilities in older plugins or themes. | Maintain automatic updates for WordPress core, themes, and plugins. Install the Wordfence security plugin. When logging in, use CAPTCHA. |

# LAB 5 – Vulnerability Analysis

| Step | Tool / Command | Output / Result (Screenshot) |
|------|----------------|------------------------------|
| 1 | **Open Your Browser:** Open `https://bulanbintanghq.com` – take a screenshot of the homepage as target proof. | <img width="863" height="367" alt="image" src="https://github.com/user-attachments/assets/f6474a41-3fbd-4367-9c21-48aac95d3cb0" /> |
| 2 | **Find the IP Address (DNS Lookup):** Run `nslookup bulanbintanghq.com` to find the IP address. | <img width="661" height="464" alt="image" src="https://github.com/user-attachments/assets/e8bca8e9-ee77-4fc7-8b55-334bfcec6158" /> |
| 3 | **Find Who Owns the Domain (WHOIS Lookup):** `whois.domaintools.com`  Search `bulanbintanghq.com` to get domain ownership details. | <img width="846" height="613" alt="image" src="https://github.com/user-attachments/assets/9834293c-d518-412d-863b-328e1eb46b3d" /> |
| 4 | **Find What Technology the Website Uses:** WappalyzerInstall Wappalyzer, visit the website, click the blue hexagon icon to see CMS, e-commerce platform, etc. | <img width="856" height="339" alt="image" src="https://github.com/user-attachments/assets/d32765a4-7851-41bf-9ebe-2ca9d3974e29" /> | 
| 5 | **Find Extra Information on the Website Itself:** Go to `https://bulanbintanghq.com/my-account/` – you will see a Login / Register form (a security finding). | <img width="821" height="271" alt="image" src="https://github.com/user-attachments/assets/3e254c27-ee66-45a1-bd9e-9cb6af91debe" /> |
