---
title: 为门户使用自定义 JavaScript |MicrosoftDocs
description: 在门户中将自定义 JavaScript 添加到表单的说明
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553638"
---
# <a name="add-custom-javascript"></a>添加自定义 JavaScript

Web 窗体步骤记录包含一个名为 "**自定义 javascript** " 的字段，该字段可用于存储 JavaScript 代码，使您能够扩展或修改窗体的视觉对象显示或功能。

JavaScript 的自定义块将添加到页面底部，紧靠在 "结束窗体标记" 元素之前。

## <a name="form-fields"></a>窗体字段

实体字段的 HTML 输入 ID 设置为属性的逻辑名称。 这使得可以使用[jQuery](https://jquery.com/)轻松选择字段、设置值或其他客户端操作。  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>其他客户端字段验证
有时您可能需要自定义窗体上的字段验证。 下面的示例演示如何添加自定义验证程序。 此示例将强制用户仅当首选联系方式的其他字段设置为电子邮件时，才指定电子邮件。

> [!NOTE]
> 子网格中不支持客户端字段验证。

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

## <a name="general-validation"></a>一般验证

单击**下一个**/**提交**"按钮时，将执行名为**webFormClientValidate**的函数。 您可以扩展此方法以添加自定义验证逻辑。

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
