---
title: Display custom comment head of TYPO3 web page
date: 2018-12-15 18:34:52
tags:
    - header comment
    - TYPO3
    - TypoScript
---

If you want add your custom comment to head of TYPO3 page like

{% codeblock Custom header comment lang:html %}
<html dir="ltr" lang="de"><head>

<meta charset="utf-8">
<!-- 
	Your custom comment here
	Comment 1 
	Comment 2

	This website is powered by TYPO3 - inspiring people to share!
	TYPO3 is a free open source Content Management Framework initially created by Kasper Skaarhoj and licensed under GNU/GPL.
	TYPO3 is copyright 1998-2019 of Kasper Skaarhoj. Extensions are copyright of their respective owners.
	Information and contribution at https://typo3.org/
-->
<meta name="generator" content="TYPO3 CMS">
...
</head>
<body>
...
</body>
</html>
{% endcodeblock %}

you can define it in TypoScript config

{% codeblock typoscript page config lang:typoscript %}
config {
    headerComment (
Your custom comment here
Comment 1 
Comment 2     
    )
}
{% endcodeblock %}

