# ELUNORI — WordPress Portfolio Website

ELUNORI is a fictional European digital-app brand created as a portfolio project. This repository captures the accepted local WordPress build without production credentials or private user accounts.

## Snapshot

- WordPress: 7.1.2
- Active theme: Twenty Twenty-Five 1.5
- Active plugins: WPForms Lite 2.0.2 and Duplicator 5.0.4
- Duplicator is present for migration convenience but is not required after a successful restore.
- Local source URL: `http://novair-portfolio.local`
- Pages: Home, About, Contact, Privacy Policy, Terms & Conditions

The site design, Gutenberg templates and template parts, global styles, navigation behavior, WPForms configuration, and page content are stored in `database/elunori.sql`. Media used by the site is stored under `wp-content/uploads/2026/09/`.

## Restore locally or on hosting

1. Install WordPress 7.1.2 or a compatible current release.
2. Install and activate Twenty Twenty-Five.
3. Install and activate WPForms Lite. Install Duplicator only if you want to use its migration workflow.
4. Copy the tracked files from `wp-content/uploads/` into the new installation.
5. Import `database/elunori.sql` into an empty WordPress database.
6. Replace the local URL with the destination URL:

   ```sh
   wp search-replace 'http://novair-portfolio.local' 'https://your-domain.example' --all-tables --precise
   ```

7. Create a new administrator account because user records are intentionally excluded from the snapshot:

   ```sh
   wp user create siteadmin admin@your-domain.example --role=administrator --prompt=user_pass
   ```

8. Re-save permalinks, review the contact-form recipient, and run a full browser QA before making the site public.

## Production checklist

- Replace the local URL and confirm HTTPS.
- Set the production administrator email.
- Configure SMTP with the hosting/domain mailbox.
- Verify WPForms validation, anti-spam, success state, and delivery.
- Review placeholder/demo app-store and social links.
- Add caching and security only after the hosting environment is known.
- Confirm privacy/terms copy for the actual deployment context.
- Enable indexing only after final production QA.

## Security note

This repository deliberately excludes `wp-config.php`, WordPress salts, database credentials, administrator users and user metadata, Local runtime files, caches, and generated plugin data.
