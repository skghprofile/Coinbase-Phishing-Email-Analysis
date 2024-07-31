# Coinbase Phishing Email Analysis

## Table Of Contents

- [Coinbase Phishing Email Analysis](#coinbase-phishing-email-analysis)
  - [Table Of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Surface Level Analysis](#surface-level-analysis)
  - [Hyperlink URL Analysis](#hyperlink-url-analysis)
  - [Malicious Parent Domain Analysis](#malicious-parent-domain-analysis)
  - [Conclusion](#conclusion)
  - [Updates/Notes](#updatesnotes)

---

## Introduction

This project analyzes a phishing email I received in my personal email inbox that was automatically flagged as spam and put into my junk email folder.

## Surface Level Analysis

Here is the email I received from "Coinbase Wallet" to my email address:

![Email Preview](/Images/CPEA-img01.PNG)
![Email Body](/Images/CPEA-img02.PNG)

Suppose someone else received this email and has had some knowledge/training on malicious emails. In that case, this email can raise some red flags quickly and be classified as illegitimate.

On the surface, these are the suspicious aspects I noticed about this email:

- The sender's address claims to be Coinbase Wallet, but the email originates from the address "info@aalinfo.com".

![Email Preview Sender Address](/Images/CPEA-img03.PNG)

Almost all emails originating from legitimate companies use their domain as the sender's address, although this can be spoofed or hijacked in more sophisticated phishing campaigns.

From Coinbase's [support page](https://help.coinbase.com/en/coinbase/privacy-and-security/other/is-this-email-really-from-coinbase), these are the email addresses that Coinbase uses:

```
Main Domain:
- support@coinbase.com
- help@coinbase.com
- contact@coinbase.com
- no-reply@coinbase.com
- compliance-kyc@coinbase.com

Sub-Domains:
- contact@updates.coinbase.com
- info@cb.mail.coinbase.com
- @mail.coinbase.com
- no-reply@info.coinbase.com
```

Even if Coinbase used a domain or sub-domain that wasn't listed above or you suspect you received a Coinbase email from a spoofed email address, Coinbase cryptographically signs all of their emails using DKIM and protects their domain against unsigned email with DMARC.

- The email's subject, "It's important to review the latest 2FA update!"  could be interpreted as this email having a sense of importance, a common phishing tactic used by malicious actors to appear legitimate.

- In the message body of the email, the sender also tries to convey a sense of urgency, another common factor used in phishing emails:

![Email Body Section](/Images/CPEA-img04.PNG)

- The email's footer also has some noticeable inconsistencies:
  1. The first text, "Coinbase 2023" is most likely supposed to be the Coinbase trademark, but I think this email template has been used throughout 2023, and they forgot to change the template since I received this email in 2024.
 ![Email Footer](/Images/CPEA-img05.PNG)
  2. The footer also seems to be made for an email address in Ireland since all of the contact info for Coinbase at that location is correct. This also makes me think this is a used template since I reside in the United States and have no reason to receive an email from a legitimate corporation in Europe if they have one that's based out of the United States.
 ![Email Footer](/Images/CPEA-img06.PNG)

## Hyperlink URL Analysis

- Before moving on to the clearest sign of this email being a part of a mass phishing campaign sent by a malicious actor, I'd like to note that I have never created or owned a Coinbase account with this email address or any other email address in my possession.

- The last part of the analysis of this email on the surface that shows that it's not a legitimate Coinbase email is the "Continue" button hyperlink in the email, wanting the user to take action to "complete the updated two-factor authentication (2FA)". 

![Continue Hyperlink In Email](/Images/CPEA-img07.PNG)

- Hovering over the "Continue" hyperlink shows that the forwarding URL is "https://cbsbirango(.)net" and isn't closely related to Coinbase in any way. This leads me to conclude that this email is malicious and part of a phishing campaign for Coinbase accounts.

![Hyperlink URL](/Images/CPEA-img08.PNG)

Unfortunately for my analysis, but fortunately for potential victims of this phishing campaign, trying to follow the link in a sandbox resulted in no website being available to view. This could be due to the malicious actor's URL being reported, switched to a new URL for their next campaign, or are having issues with setting up the URL. This is surprising to me since the email was only three days old. When I tried to investigate the link, I found that it was already unavailable.

![Malicious URL Page](/Images/CPEA-img09.PNG)

Two days later, a total of 5 days since the email was sent, I tried to access the URL again. This time, I quickly saw that the URL had been forwarded to "https://colnbase-com(.)demontconsultancy(.)org/" and then forwarded once again to a regular Google.com domain. Clicking on the URL and then stopping the 2nd forwarding allowed me to see the "https://colnbase-com(.)demontconsultancy(.)org/" but there was no content on the page. Directly entering that URL yielded no results and ultimately forwarded my browser to Google.com.

![Malicious URL Link](/Images/CPEA-img10.PNG)

Trying to see any snapshots of the malicious URL, I entered the URL into the [Internet Archive's Wayback Machine](https://web.archive.org/). The search resulted in 4 snapshots, 2 on July 23rd, 2024, and 2 on July 25th, 2024. Each of the 4 snapshots was ultimately forwarded to Google.com due to an HTTP 301 response code, so I could not see any actual content related to the malicious URL.

![Wayback Machine Page](/Images/CPEA-img11.PNG)
![Wayback Machine Page](/Images/CPEA-img12.PNG)

## Malicious Parent Domain Analysis

My next thought was to search the primary domain "demontconsultancy(.)org" to see if any web pages are associated with this domain. This domain yielded a web page for studying in Ukraine.

![Webpage](/Images/CPEA-img13.PNG)

I'm unsure if this is a legitimate company, but I wanted to investigate the content on the website further. While looking through the website, I remembered a podcast from Jack Rhysider's Darknet Diaries talking about scams involving fake colleges and degrees. This specific podcast was [Ep.142: Axact](https://www.youtube.com/watch?v=bQ4GnulBKJA).

![Darknet Diaries Youtube Thumbnail](/Images/CPEA-img14.PNG)

With this being an international education consultancy company and not claiming to be a university, I can only point out inconsistencies and unusual elements on the website and not make any conclusions on whether this business is legitimate or not.

Here are some of the inconsistencies and unusual elements I found:

- The website uses many stock photos and actual photos from other official Ukranian universities on the website.

![Webpage Image](/Images/CPEA-img15.PNG)
![Webpage Image](/Images/CPEA-img16.PNG)
![Webpage Image](/Images/CPEA-img17.PNG)
![Webpage Image](/Images/CPEA-img18.PNG)

- The website's footer copyright has yet to be updated since 2022, but the website content has been updated for 2024.

![Webpage Image](/Images/CPEA-img20.PNG)
![Webpage Image](/Images/CPEA-img19.PNG)

- The business that built the Demont Educational Consultants webpage "SE Software Technologies" uses the domain "https://superconeng(.)com/" and claims to be "a complete digital services company located in Germany, Canada, and the USA.", but their businesses's Facebook page shows their location as being located in Pakistan.

![Webpage Image](/Images/CPEA-img21.PNG)
![Webpage Image](/Images/CPEA-img22.PNG)

- The Follow Us section on the Demont Educational Consultants webpage has inconsistent links for social media. They have a Facebook and Instagram page but no link to their Twitter. Their YouTube link is also set to the Instagram page, and their LinkedIn is unavailable.

![Webpage Image](/Images/CPEA-img23.PNG)

## Conclusion

What I thought was going to be a simple phishing email, led me down a rabbit hole I wasn't expecting. I'm glad the original email was sent straight to my junk folder, and the "Continue" phishing hyperlink "https://colnbase-com(.)demontconsultancy(.)org/" ultimately didn't lead anywhere.

My thoughts are that this was supposed to be a valid phishing campaign for Coinbase accounts, but it wasn't set up correctly, and the malicious actors barely did any spoofing or obfuscation for this campaign.

My opinion, with no factual evidence behind it, on how this phishing campaign is arranged is as follows:
- SE Software Technologies and/or Demont Educational Consultants could be behind this campaign. My thoughts behind this are because of the potential malicious subdomains "colnbase-com(.)demontconsultancy(.)org" and "www(.)colnbase-com(.)demontconsultancy(.)org" being used. Since SE Software Technologies claims to power/manage the Demont Educational Consultants webpage, I included them above even though the subdomains are a part of the "demontconsultancy(.)org" domain.
- The same team behind the campaign also bought or took over the "https://cbsbirango(.)net" domain, but I am curious why the hyperlink in the original email isn't directly linking to the final URL of "colnbase-com(.)demontconsultancy(.)org". The only reasoning I can think of is that email clients search for domains and sub-domains similar to official ones for spam and phishing emails, and going to an unrelated random domain before being redirected to the final one is a way around that search.
- The sender of the original email itsself "info@aalinfo(.)com" could be a legitimate company. The email itself passes SPF checks but doesn't pass DKIM authentication, and the domain isn't set up with DMARC, so it also fails that check by default. Their website does SAP consulting and hosts SAP training courses. They also link a YouTube channel on their website that has videos uploaded by the company over the course of 4 years, 1+ year under Aalinfo. Also, the domain "aalinfo(.)com" doesn't appear to be blacklisted, so if aalinfo isn't a part of this campaign knowingly, this domain to me has the highest chance out of all the domains listed above to be compromised.

## Updates/Notes

7-31-2024 Update/Note:

After finishing my analysis, I wanted to note that the "https://demontconsultancy(.)org/" domain and subdomains currently display an error message of 503 - service unavailable.

![Webpage Image](/Images/CPEA-img24.PNG)