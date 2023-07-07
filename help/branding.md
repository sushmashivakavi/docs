# Setting Custom Domain

## App Setup

To setup your own domain name and theme colors follow the below steps:

- Login to panel using primary domain name given by vendor
- Click Partners -> branding on left side menu
- Enter your domain name in desired space. ex: `my.example.com`
- Name your website, will be used in all communication emails
- Title will be displayed on browser window
- Done

## CNAME Setup

Login to your domain register and create an CNAME record for your domain point to

```code
{cname_domain}
```

## Have you setup your CNAME?

You can test that your domain is setup correctly using `dig`:

```shell
dig @8.8.8.8 +short CNAME my.example.com
```

On successfull pointing, you can able to see the results similar to below

```shell
;; ANSWER SECTION:
my.example.com.	984	IN	CNAME	{cname_domain}.
{cname_domain}.	59	IN	A	52.76.163.53
{cname_domain}.	59	IN	A	52.221.80.168

```

_Note:_ Some hosting providers may take upto 12 hours to resolved the cname mapping.
