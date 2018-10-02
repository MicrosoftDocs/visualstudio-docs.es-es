---
title: Shell (aislado o integrado) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 364a45ea3ae66e3ba8962bfce1487cc04ba35397
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581419"
---
# <a name="shell-isolated-or-integrated"></a>Shell (aislado o integrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Shell (aislado o integrado)](https://docs.microsoft.com/visualstudio/extensibility/shell-isolated-or-integrated).  
  
Puede crear su propia aplicación basada en Visual Studio en modo integrado o aislado. En el modo integrado, muchas características de Visual Studio están disponibles además de su aplicación. En el modo aislado, elegir un subconjunto de características de Visual Studio que desea distribuir junto con su propia extensión.  
  
## <a name="integrated-mode"></a>Modo integrado  
 El modo integrado permite a los usuarios usar las características estándar de Visual Studio junto con sus herramientas personalizadas. El shell integrado está pensado principalmente para hospedar los lenguajes de programación y herramientas de desarrollo de software.  
  
 Herramientas personalizadas que se generan automáticamente en el shell integrado de mezcla con cualquier otra edición de Visual Studio que está instalado en el mismo equipo. Puede proporcionar una versión redistribuible del shell integrado de Visual Studio si ya no está instalado Visual Studio.  
  
 La versión redistribuible del shell integrado de Visual Studio no incluye lenguajes de programación y las características que admiten sus sistemas de proyecto respectivos.  
  
> [!NOTE]
>  El modo integrado de shell de Visual Studio se puede instalar junto con todas las ediciones de Visual Studio, excepto las ediciones Express.  
  
 Para obtener más información, consulte [Visual Studio Shell (integrado)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo aislado  
 Modo aislado permite crear herramientas personalizadas que se ejecutan en paralelo con otras versiones de Visual Studio. Se está diseñado principalmente para las herramientas que pueden tener acceso a servicios de Visual Studio sin según todas las características estándar de Visual Studio. Puede personalizar la apariencia de las aplicaciones basadas en el shell aislado de Visual Studio. Puede desactivar fácilmente las características y los grupos de comandos de menú que no desea que aparezca junto con la aplicación.  
  
 Para obtener más información, consulte [Visual Studio Shell aislado](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuir la aplicación de Shell integrado o aislado  
 Con el fin de distribuir la aplicación de shell integrado o aislado, deberá incluir la aplicación, un especial shell integrado o aislado redistribuible y un programa de instalación. Para obtener más información acerca de la distribución e instalación, consulte [distribuir aplicaciones de Shell aislado](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  El [contrato de licencia de usuario final (CLUF)](https://www.visualstudio.com/en-us/support/legal/mt171552) integrado y aislado de Visual Studio shells incluye una sección acerca de la recopilación de datos (**sección 3. Datos**).  Describe los datos de uso de cliente que se pueden recopilar mediante Microsoft de los usuarios de que el software de shell integrado o aislado que se genera en la aplicación. Para obtener más información, consulte [Microsoft Visual Studio declaración familia de productos privacidad](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Si recopila datos de uso independiente de sus clientes a través de la aplicación, debe proporcionar aviso adecuado a los usuarios de la aplicación de lo que recopila.  Al distribuir el software de shell aislado o integrado como parte de la aplicación, según la licencia del Kit de desarrollo de Software de Visual Studio, debe incluir uno de los siguientes:  
>   
>  -   el contrato de licencia de usuario final como parte de su licencia de aplicación  
> -   sus propios términos de licencia que requiere que los clientes que acepten los términos que protección la Visual Studio integrado o aislado shell al menos tanta como los términos de licencia de usuario final de Microsoft para el software de shell  
  
## <a name="additional-resources"></a>Recursos adicionales  
 Para obtener más información acerca de los paquetes redistribuibles, consulte el [descargas de Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sitio Web.  
  
## <a name="see-also"></a>Vea también  
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

