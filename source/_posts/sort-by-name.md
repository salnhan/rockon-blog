---
title: PHP Sort by name with Umlauts
date: 2019-06-20 12:15:48
tags:
 - PHP
 - Sorting
 - multi array
categories:
 - backend
teaser: Howto sort array by name with Umlauts alphabetically in PHP
---

Assuming you have an array like this

{% codeblock  multi dimensional array php lang:php %}

Array
(
    [0] => Array
        (
            [0] => Ausschuss der Finanzen
            [1] => Ältestenrat
            [2] => Rechtsausschuss
            [3] => Prüfungsausschuss
        )

    [1] => Array
        (
            [0] => Vorstand
        )

)
{% endcodeblock %}

And you want the sort the elements in $arrayBeforeSorting alphabetically like

{% codeblock  multi dimensional array php lang:php %}

Array
(
    [0] => Array
        (
            [0] => Ältestenrat
            [1] => Ausschuss der Finanzen
            [2] => Prüfungsausschuss
            [3] => Rechtsausschuss
        )

    [1] => Array
        (
            [0] => Vorstand
        )

)

{% endcodeblock %}


Here ist a possible solution

{% codeblock  array sort php lang:php %}

/**
* Sort array alphabetically
*
* @param array $arrayBeforeSorting
* @return array
*/
function sortNameByAlphabet(array $arrayBeforeSorting)
{
    $arrayAfterSorting = [];

    foreach ($arrayBeforeSorting as $nameList) {
        // If more than 2 elements do sorting
        if (count($nameList) > 1) {
            array_multisort(convertSpecialCharacters($nameList), SORT_ASC, SORT_STRING, $nameList);
        }

        $arrayAfterSorting[] = $nameList;
    }

    return $arrayAfterSorting;
}

/**
* Convert german special characters (umlaut) to alphabet characters
*
* @param array $nameList
* @return array
*/
function convertSpecialCharacters($nameList)
{
    $toConvertList = ['Ä'=> 'Ae', 'Ö' => 'Oe', 'Ü' => 'Ue', 'ä' => 'ae', 'ö' => 'oe', 'ü' => 'ue', 'ß' => 'ss'];
    $converted = [];
    foreach ($nameList as $name) {
        $converted [] => strtr($name, $toConvertList);
    }

    return $converted;
}


/**
* Test
*/

$arrayBeforeSorting = [
	[
		'Ausschuss der Finanzen',
		'Ältestenrat',
		'Rechtsausschuss',
		'Prüfungsausschuss'
	],
	[
		'Vorstand'
	]
];

echo "Array before sorting \n";
print_r ($arrayBeforeSorting);

echo "Array after sorting \n";
print_r(sortNameByAlphabet($arrayBeforeSorting));
{% endcodeblock %}

***Remark***

* The PHP Code above works in PHP Version **5** and **7**. 
* You can copy the code above the paste it to the [php sandbox](http://sandbox.onlinephpfunctions.com/) for testing.