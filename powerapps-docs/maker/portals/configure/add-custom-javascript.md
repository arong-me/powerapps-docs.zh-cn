---
title: 为门户使用自定义 JavaScript | MicrosoftDocs
description: 有关如何向门户中的窗体添加自定义 JavaScript 的说明
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: fca222555a4a19b511e3b2a140586d20a668ec85
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979369"
---
# <a name="add-custom-javascript"></a>添加自定义 JavaScript

Web 窗体步骤记录包含名为**自定义 JavaScript** 的字段，该字段可用于存储 JavaScript 代码，以允许您扩展或修改窗体的直观显示或功能。

自定义 JavaScript 块将在关闭窗体标记元素前添加到页面底部。

## <a name="form-fields"></a>窗体字段

实体字段的 HTML 输入 ID 设置为属性的逻辑名称。 这通过使用 [jQuery](https://jquery.com/) 让选择字段、设置或其他客户端操作变得轻松。  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>其他客户端字段验证
有时您可能需要自定义窗体上的字段验证。 以下示例说明如何添加自定义验证程序。 此示例仅在“联系人的首选方法”的另一个字段设置为电子邮件时强制用户指定电子邮件。

> [!NOTE]
> 客户端字段验证在子网格中不受支持。

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>通常的验证

单击**下一步**/**提交**按钮之后，将执行名为 **webFormClientValidate** 的函数。 您可扩展此方法来添加自定义验证逻辑。

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体窗体](entity-forms.md)  
[门户的 Web 窗体步骤](web-form-steps.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[重定向步骤类型](add-redirect-step.md)  
[条件步骤类型](add-conditional-step.md)
