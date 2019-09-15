---
title: Extends TYPO3 extbase model or controller
date: 2019-07-16 21:51:03
tags:
 - TYPO3
 - Extbase
 - Domain
 - Model
 - Controller
categories:
 - TYPO3
teaser: Overrides or extends a TYPO3 Extbase model or controller

---

If you have to override or extend Extbase model or controller, you should do following steps

{% img logo-icon https://typo3.org/typo3conf/ext/t3olayout/Resources/Public/Images/Template/typo3_nomargins.svg 352 72 typo3 logo %}

---

### Extend controller

{% codeblock  Create new extbase controller NewController.php lang:php %}
 <?php

 namespace Extension\Name\Controller;

 class NewController extends \Extension\Original\Controller\OldController
{
    /**
    *  new action
    * @return null
    */
    public function newAction()
    {
        return null;
    }
}
{% endcodeblock %}

 {% codeblock Register controller via TypoScript setup.txt lang:ts %}
config.tx_extbase {
    objects {
        \Extension\Original\Controller\OldController {
            className = Extension\Name\Controller\NewController
        }
    }
}
{% endcodeblock %}

---

### Extend model 

Add new field `field_color` to model `tx_extname_domain_model_modelname`

{% codeblock Add new field to ext_tables.sql lang:sql %}
CREATE TABLE tx_extname_domain_model_modelname (
 field_color varchar(255) DEFAULT '' NOT NULL
);
{% endcodeblock %}


{% codeblock  Create a new model class ModelName.php lang:php %}

<?php
namespace Extension\Name\Domain\Model\ModelName;

class ModelName extends \Extension\Original\Domain\Model\ModelName
{
    /**
    *@param string
    */
    fieldColor = ''; 

    /**
    * @return string
    */
    protected function getFieldColor()
    {
        return $this->fieldColor;
    }

    /**
    * @param string
    */
    protected function setFieldColor($color)
    {
        $this->fieldColor = $color;
    }
}
{% endcodeblock %}

{% codeblock   Register new model via TypoScript lang:ts %}
config.tx_extbase {
    objects {
        Extension\Original\Domain\Model\ModelName {
            className = Extension\Name\Domain\Model\ModelName
        }
    }
    persistence {
        classes {
            Extension\Name\Domain\Model\ModelName {
                mapping {
                    tableName = tx_extname_domain_model_modelname
                }
            }
        }
    }
}
{% endcodeblock %}
