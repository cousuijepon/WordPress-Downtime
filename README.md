# How to Move Your WordPress Site to a New Host Without Downtime?

Migrating a WordPress site to a new hosting provider is one of those tasks that sounds more technical than it actually is.

Most website owners avoid it longer than they should, staying on slow, expensive, or unreliable hosting out of fear that moving will break something, cause downtime, or require a developer. In reality, with the right process and a reliable destination host, a clean migration takes two to four hours and results in zero downtime for visitors.

## Why People Migrate WordPress Hosts?

The reasons for switching hosting providers almost always come down to one of five things.

Slow loading times. A host that was adequate when your site launched may no longer keep up as your content and traffic grow. Shared hosting with Apache servers and standard SSD storage performs noticeably slower than LiteSpeed with NVMe storage at comparable price points. If your Time to First Byte is consistently above 600ms, hosting is almost certainly a contributing factor.

Unreliable uptime. Downtime costs e-commerce sites money directly and costs every site credibility. If your current host has multiple unplanned outages per quarter, migration to a more stable provider is the most effective fix.

Renewal pricing shock. Most hosting providers lock in new customers with steep introductory discounts and charge significantly more at renewal. Some users find their annual bill doubling or tripling at renewal time, which triggers a re-evaluation of whether the host is actually worth that rate.

Hitting resource limits. Shared hosting accounts have limits on Entry Processes (concurrent PHP workers), CPU time, MySQL query duration, and memory. When a WordPress site grows past those limits, it encounters errors, “Error Establishing a Database Connection,” 503 timeouts during traffic spikes, or plugin timeouts, that are purely hosting-side problems requiring either an upgrade or a migration.

[Hostinger Coupon Code & Discount, 80% Off Black Friday Deals](https://github.com/tpreetam51/hostfirst/)

Moving to a better value host. Sometimes the motivation is straightforward: you find a better combination of performance and price elsewhere. A direct comparison of what different providers include at similar price points often reveals meaningful gaps.

---

## Step 1: Choose Your New Host and Set Up the Account

Before touching your current site, get your new hosting account fully set up. This means purchasing a plan, confirming your login credentials, and having access to the new host’s control panel before you move any files.

### What to Look for in a Migration Destination

LiteSpeed web servers. The performance difference between LiteSpeed with LSCache and traditional Apache is measurable in page load benchmarks. LiteSpeed handles concurrent PHP requests more efficiently, which directly reduces Time to First Byte and improves Core Web Vitals scores.

NVMe SSD storage. NVMe read/write speeds are up to 10x faster than standard SSD. For WordPress, which makes multiple database queries per page load, faster storage reduces query time noticeably.

Staging environment. A staging environment lets you test your migrated site before pointing DNS to the new server, essential for a zero-downtime migration. Available on most Business and above plans.

Daily backups. Your new host should be taking daily automated backups from day one. If something goes wrong post-migration, you need a recent clean restore point.

Migration tools. Many hosts offer free migration services or one-click migration plugins that simplify the process considerably.

Hostinger’s Business plan covers all five requirements. The full pricing for every plan tier, including what each one includes versus what costs extra, is broken down in this [Hostinger pricing plans for 2026](https://hostingfirst.discount/pricing/), which compares introductory rates, renewal rates, Entry Process limits, storage types, and backup frequency across each plan. Worth reading before you decide which tier fits your site’s traffic level and needs.

### Setting Up Your New Hosting Account

After purchasing, log into hPanel (or your new host’s control panel) and complete these steps before starting the migration:

1. Verify your account is active and hPanel loads correctly
2. Note your new server’s IP address, you’ll need this for DNS later
3. Note your MySQL host, default username, and credentials
4. Verify that your domain is added to the account (as an addon domain if it’s not your primary domain)
5. Confirm SSH access is available if you plan to use a manual migration method

---

## Step 2: Create a Complete Backup of Your Current Site

Never begin a migration without a verified backup of your current site. If anything goes wrong during the process, the backup is your safety net.

[Hostinger Coupon Codes 80% off and Hosting Cost: USA & India](https://github.com/maccvv21/Unzip-Script/)

### Method 1: Using UpdraftPlus (Recommended for Most Users)

UpdraftPlus is the most widely used WordPress backup plugin with over 3 million active installations. The free version backs up files and database to Google Drive, Dropbox, Amazon S3, or your server.

How to create a complete backup with UpdraftPlus:

1. Install and activate UpdraftPlus from the WordPress plugin directory
2. Go to Settings > UpdraftPlus Backups
3. Click Backup Now
4. Check both “Include your database in the backup” and “Include your files in the backup”
5. Click Backup Now to start
6. Wait for the backup to complete, a green checkmark appears when done
7. Download all backup files to your local computer

The backup produces several zip files: one for the database, one for plugins, one for themes, one for uploads, and one for any additional files. Keep all of them.

### Method 2: cPanel File Manager + phpMyAdmin (Manual)

If you have cPanel access on your current host, you can download your files directly and export your database without a plugin.

Files: In cPanel, open File Manager, navigate to public_html, select all files and folders, compress to a zip, and download.

Database: In cPanel, open phpMyAdmin, select your WordPress database from the left sidebar, click Export, choose the Quick export method with SQL format, and click Go. Save the .sql file.

---

## Step 3: Create a Fresh WordPress Install on Your New Host

On your new host, set up a clean WordPress installation at your domain. This gives you a working WordPress environment that you’ll overwrite with your migrated content.

In Hostinger hPanel:

1. Go to Websites and click Create or Migrate a Website
2. Choose WordPress
3. Select your domain
4. Set a temporary admin username and password (you’ll overwrite this with the migration anyway)
5. Click Install

WordPress installs in under 60 seconds. Once complete, create a new empty MySQL database for your migrated content, note the database name, username, and password carefully.

---

## Step 4: Upload Your Site Files to the New Host

### Via FTP (FileZilla)

FileZilla is a free FTP client available for Windows, Mac, and Linux.

1. Open FileZilla and connect to your new host using your FTP credentials (available in hPanel under FTP Accounts)
2. In the Remote Site panel, navigate to public_html
3. Delete the default WordPress files that were just installed (you’re replacing them with your backup)
4. In the Local Site panel, navigate to your extracted backup files
5. Select all files and drag them to the Remote Site panel
6. Wait for the upload to complete, this takes 10–60 minutes depending on site size and internet speed

### Via Hostinger’s File Manager

For smaller sites, hPanel’s built-in File Manager works without needing FTP:

1. In hPanel, go to Files > File Manager
2. Navigate to public_html
3. Delete the default WordPress installation
4. Upload your backup zip file using the Upload button
5. Extract the zip in place using the right-click Extract option

---

## Step 5: Import Your Database

This step restores your WordPress content, all posts, pages, settings, user accounts, and plugin configurations.

In Hostinger hPanel:

1. Go to Databases > phpMyAdmin
2. In the left sidebar, click on the empty database you created earlier
3. Click the Import tab at the top
4. Click Choose File and select your .sql database backup file
5. Click Go at the bottom of the page

The import processes each SQL statement from your backup. For large databases, this may take several minutes. A green success message confirms completion.

[Hostinger Coupon Code 83% Off (November 2026) $375 Discount](https://github.com/unusdeals/Hostinger/)

## Step 6: Update wp-config.php

Your wp-config.php file contains the database connection settings for WordPress. After migration, these need to match your new hosting environment’s database credentials.

In hPanel File Manager, navigate to public_html and open wp-config.php for editing. Update these three lines:

define( 'DB_NAME', 'your_new_database_name' );

define( 'DB_USER', 'your_new_database_username' );

define( 'DB_PASSWORD', 'your_new_database_password' );

Replace each value with the credentials from the database you created on your new host. Save the file.

If your new host uses a different database host address than localhost, update:

define( 'DB_HOST', 'localhost' );

to whatever your new host specifies. Hostinger uses localhost by default, so in most cases this line needs no change.

---

## Step 7: Test the Migrated Site Before Switching DNS

This is the step most people skip, and it’s the one that separates a clean, professional migration from a stressful one. Testing before pointing DNS to the new server means your visitors never see a broken or incomplete migration.

### Using Your Hosts File to Preview the New Site

Your computer’s hosts file maps domain names to IP addresses locally, overriding DNS. By temporarily pointing your domain to your new server’s IP in this file, your browser shows you the new site while everyone else sees the old one.

On Mac or Linux:

sudo nano /etc/hosts

Add a line at the bottom:

Replace 123.456.789.000 with your new server’s IP address.

On Windows:

Open Notepad as Administrator, then open the file C:\Windows\System32\drivers\etc\hosts and add the same two lines.

Save the file, open your browser, and visit your domain. You’ll see the new server’s version of your site. Check:

* Homepage loads correctly
* All images and media display
* Navigation links work
* Contact forms submit
* Any e-commerce functionality operates
* Admin login works at yourdomain.com/wp-admin
* SSL certificate loads (padlock shows in address bar)

When testing is complete, remove the lines you added to the hosts file to restore normal DNS behavior.

### Using a Staging URL

If your new host provides a temporary staging URL (Hostinger provides one through hPanel), you can test the migrated site at that URL without touching your hosts file at all. This is simpler for users who aren’t comfortable editing system files.

---

## Step 8: Update Your Search and Replace URLs (If Needed)

If your old hosting environment used a different domain URL in the database (common when migrating from a development subdomain or testing URL), you need to update all database references to match your live domain.

The cleanest way to do this is with the Better Search Replace plugin (free, from the WordPress repository):

1. Install and activate Better Search Replace on your new WordPress install
2. Go to Tools > Better Search Replace
3. In the Search for field: enter your old URL (e.g., https://oldsite.staging.hostingprovider.com)
4. In the Replace with field: enter your live domain (e.g., https://yourdomain.com)
5. Select all tables
6. Run as a dry run first to see what would change without actually changing it
7. Run for real once you’ve confirmed the dry run looks correct

This updates every instance of the old URL across your entire database — fixing broken images, navigation links, and any absolute URLs in your content.

---

## Step 9: Switch DNS and Complete the Migration

Once testing is complete and the migrated site works correctly, switch DNS to point your domain to the new server. This is the step that moves live traffic from old host to new host.

### If Your Domain is Registered Separately

Log into your domain registrar and update the nameservers or A record to point to your new host.

Nameserver method (Hostinger): In hPanel, go to Hosting > Nameservers and note Hostinger’s nameservers (ns1.hostinger.com and ns2.hostinger.com). At your registrar, replace the current nameservers with these.

A record method: In your domain’s DNS settings at your registrar, change the A record for @ (your root domain) to your new server’s IP address, and change or add the www A record to the same IP.

### If Your Domain is Registered at Hostinger

In hPanel, the domain and hosting are already linked. If you registered at a previous host and transferred your domain, update the nameservers as above. If your domain was always at Hostinger, DNS likely already points to your new plan correctly.

### DNS Propagation

DNS changes take up to 48 hours to propagate globally, though most locations see the change within 1–4 hours. During this window, some visitors see the old site and some see the new one. This is normal and not a sign anything went wrong.

Keep your old hosting account active for 48–72 hours after switching DNS. This ensures visitors who still resolve to the old server get a working site while propagation completes.

---

## Step 10: Set Up SSL on the New Host

Modern WordPress sites need HTTPS. Google uses HTTPS as a ranking signal, and Chrome shows a “Not Secure” warning for HTTP-only sites that causes a significant portion of visitors to leave immediately.

Hostinger automatically provisions free SSL certificates through Let’s Encrypt for all hosted domains. In hPanel, go to SSL and verify that your domain shows an active certificate. If it shows as pending, click Force HTTPS to trigger provisioning.

Once SSL is active, add these lines to your wp-config.php to ensure WordPress always loads over HTTPS:

define('FORCE_SSL_ADMIN', true);

And in your WordPress dashboard under Settings > General, update both the WordPress Address and Site Address to https:// versions of your domain.

---

## The Plugin Method: Using Duplicator or All-in-One WP Migration

If the manual method above feels like too many steps, two plugins simplify the entire process into a few clicks.

### Duplicator (Free Tier)

Duplicator packages your entire WordPress site — files and database together — into a single installer archive. You upload two files to your new host and run the installer in your browser.

Migration steps with Duplicator:

1. Install Duplicator on your current site
2. Go to Duplicator > Packages and click Create New
3. Walk through the wizard and download both the installer (installer.php) and the archive (.zip) files
4. Upload both files to the root of your new hosting account via FTP or File Manager
5. Visit yourdomain.com/installer.php in your browser
6. Follow the installer wizard — enter your new database credentials when prompted
7. Duplicator copies all files, imports the database, and updates configuration automatically

Duplicator’s free tier handles most standard migration scenarios. The paid Pro version removes the 500MB site size limit and adds scheduled backups.

### All-in-One WP Migration (Free up to 512MB)

All-in-One WP Migration is the simplest plugin option — it exports everything to a single .wpress file and imports it on the new site.

1. Install on your current site, go to All-in-One WP Migration > Export, and download the .wpress file
2. Install All-in-One WP Migration on your fresh WordPress install on the new host
3. Go to All-in-One WP Migration > Import and upload the .wpress file
4. Wait for the import to complete and click Save Permalinks when prompted

The free tier is limited to 512MB. For larger sites, either Duplicator or the manual method works without size limits.

---

## Common Migration Problems and How to Fix Them

White screen of death after migration

Usually caused by a plugin or theme incompatibility triggered by a PHP version difference between hosts. In hPanel, check your PHP version under Advanced > PHP Configuration and match it to what your old host used. Also check your error logs under Logs > Error Log for the specific trigger.

Images not loading

Your image paths in the database still reference the old domain structure, or the file permissions on the uploads folder are wrong. Run a search and replace with Better Search Replace to update URLs, and check that public_html/wp-content/uploads has 755 permissions (right-click > Permissions in File Manager).

“Error Establishing a Database Connection”

Your wp-config.php database credentials don’t match the database on your new host. Double-check the database name, username, and password character by character. A single typo causes this error.

Redirect loop on HTTPS

The site keeps bouncing between HTTP and HTTPS. Add define('FORCE_SSL_ADMIN', true); to wp-config.php, ensure your WordPress Address and Site Address in Settings > General both use https://, and verify your SSL certificate is fully provisioned in hPanel.

Admin password not working

The database import may have overwritten your admin credentials with those from the old site. Log into phpMyAdmin on your new host, find the wp_users table, and either update the password using the MD5 function or reset it through the “Lost your password?” link on the login page.

---

## How to Choose the Right Hostinger Plan for Your Migrated Site

The plan you migrate to should match your site’s actual traffic and resource needs — not just the lowest available price point. Moving to a plan that’s underpowered for your traffic creates the same performance problems you just migrated away from.

Under 10,000 monthly visitors → Premium Shared plan covers this comfortably. Weekly backups are the main limitation; if your site publishes daily content or processes regular orders, the Business plan’s daily backups are worth the difference.

10,000–50,000 monthly visitors → Business plan is the right fit. The 30 Entry Processes handle concurrent PHP requests significantly better than Premium’s 10, and the daily backups, CDN, and object cache are meaningful additions at this traffic level.

50,000–200,000 monthly visitors → Cloud Startup. Dedicated IP address, 40 Entry Processes, 3 GB RAM allocation, and priority support handle traffic spikes without the “noisy neighbor” variability of shared hosting.

200,000+ monthly visitors, WooCommerce, or custom apps → VPS KVM 2 or above. Root access, dedicated resources, and predictable renewal pricing make VPS the better long-term value at scale.

For new users migrating to Hostinger for the first time and wanting to keep costs low during setup, the current discount structure offers meaningful savings. A consolidated breakdown of what each plan costs with coupon codes applied is available in this [Hostinger 57% off coupon for all hosting plans](https://hostinger-deals.nicepage.io/), which lists every active discount across plan tiers in one place so you can confirm what you’ll pay before committing to a billing term.

---

## Keeping Costs Low After Migration

Migration itself is a one-time event, but hosting costs are ongoing. There are three points where smart choices save real money:

At initial signup. Introductory pricing is deepest on the longest available billing term. Signing up for 48 months instead of 12 months at the same promotional rate saves the difference for 36 additional months. The per-month cost on a 48-month plan is substantially lower than the same plan on a 12-month term.

At renewal. Renewal rates on shared hosting are 3–5x higher than introductory rates. Set a calendar reminder 60 days before your plan expires. Check your hPanel dashboard for any loyalty discounts, and if none appear, contact support directly before renewing at the full rate.

When purchasing. New users can stack a referral or promotional link discount on top of Hostinger’s base plan pricing for further savings. The [Hostinger 75% off coupon codes and discount deals ](https://stackblitz.com/@salmanamir6969/collections/hostinger-coupon-code-for-first-time-user-best-75-discounts-promo-deals-in-2026)covers every currently active discount across plan categories with exact pricing tables showing what you pay per month after the coupon — useful for calculating your total first-term cost before checkout.

For ongoing plan management, the [Hostinger coupon code up to 83% off ](https://hostinger-discount.nicepage.io/)article tracks promotional pricing across Shared, WordPress, Cloud, and VPS plans with a step-by-step walkthrough of the checkout process — handy if you’re adding a second hosting account or upgrading an existing plan mid-term.

---

## Post-Migration Checklist

Run through this checklist after DNS has fully propagated:

* Site loads at both yourdomain.com and www.yourdomain.com
* HTTPS is active and padlock shows in browser address bar
* All pages and posts load correctly
* All images and media display correctly
* Contact forms submit and send emails successfully
* WordPress admin login works at yourdomain.com/wp-admin
* Google Analytics and Search Console are receiving data
* WooCommerce checkout and payment processing work (if applicable)
* Scheduled plugin tasks and cron jobs running (check with WP Crontrol plugin)
* Sitemap accessible at yourdomain.com/sitemap.xml
* Google Search Console verified at new host
* Old hosting account cancelled or kept as fallback for 72 hours

---

## How Long Does a WordPress Migration Take?

For most sites under 5GB total (files plus database), the full migration process following the steps above takes 2–4 hours of active work. Most of that time is uploads and imports rather than active decisions — you’re waiting while files transfer.

For very large sites (20GB+), large media libraries, or complex multisite setups, allow a full day and consider using a professional migration service. Most managed WordPress hosts including Kinsta and WP Engine offer free professional migrations — though at significantly higher plan costs than shared hosting.

For budget-conscious migrations where doing it yourself is the preferred option, this guide covers everything you need. The process is linear and recoverable at every step. If something looks wrong after the database import, you still have the backup and can start the import step again without having touched DNS or affected your live site.

Resource:

* https://github.com/maccvv21/Unzip-Script/
* https://github.com/tpreetam51/hostfirst/
* https://github.com/unusdeals/Hostinger/
* https://hostingfirst.discount/
* https://hostingfirst.discount/pricing/
* https://hostingfirst.discount/black-friday-deals/
* https://site-w1ldtopiu.godaddysites.com/
* https://hostinger-coupon-code-discount-37-off-a.webflow.io/
* https://scribehow.com/o/LixvQw4dQGuBuo1Zyp12EA/page/Hostinger_Coupon_Code_For_First-Time_Users_2026_81percent_Off_Now__XbHjUAwdTHSkoOkTB9-Gow
* https://brilliant-dinosaur-pw2x1v.mystrikingly.com/
* https://hostinger20-discount.mystrikingly.com/
* https://sites.google.com/view/shadowx-deals/hostinger
* https://hostinger-discount.nicepage.io/
* https://stackblitz.com/@salmanamir6969/collections/hostinger-coupon-code-for-first-time-user-best-75-discounts-promo-deals-in-2026
* https://hostinger-deals.nicepage.io/
