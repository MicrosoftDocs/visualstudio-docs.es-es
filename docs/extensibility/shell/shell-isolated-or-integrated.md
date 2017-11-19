---
title: Shell (aislado o integrado) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92462699141f9d0a1af2d9eb461caadf4ee467ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (aislado o integrado)
Puede crear su propia aplicación basada en Visual Studio en modo integrado o aislado. En el modo integrado, muchas características de Visual Studio están disponibles, además de la aplicación. En el modo aislado, debe elegir un subconjunto de características de Visual Studio que se va a distribuir junto con su propia extensión.  
  
## <a name="integrated-mode"></a>Modo integrado  
 El modo integrado permite a los usuarios usar las características estándar de Visual Studio junto con las herramientas personalizadas. El shell integrado está diseñado principalmente para hospedar los lenguajes de programación y herramientas de desarrollo de software.  
  
 Las herramientas personalizadas que se generan automáticamente en el shell integrado se combinan con cualquier otra edición de Visual Studio que está instalado en el mismo equipo. Puede proporcionar una versión redistribuible del shell integrado de Visual Studio si ya no está instalado Visual Studio.  
  
 La versión redistribuible del shell integrado de Visual Studio no incluye lenguajes de programación y las características que admiten sus respectivos sistemas de proyectos.  
  
> [!NOTE]
>  El modo integrado de shell de Visual Studio se puede instalar junto con todas las ediciones de Visual Studio excepto las ediciones Express.  
  
 Para obtener más información, consulte [Visual Studio Shell (integrado)](visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo de aislamiento  
 Modo aislado permite crear herramientas personalizadas que se ejecutan en paralelo con otras versiones de Visual Studio. Sirve principalmente para las herramientas que pueden tener acceso a servicios de Visual Studio sin según todas las características estándar de Visual Studio. Puede personalizar la apariencia de las aplicaciones basadas en el shell aislado de Visual Studio. Puede desactivar fácilmente las características y los grupos de comandos de menú que no desea que aparezca junto con la aplicación.  
  
 Para obtener más información, consulte [Shell aislado de Visual Studio](visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuir la aplicación de Shell aislado o integrado  
 Para distribuir la aplicación de shell aislado o integrado, debe incluir la aplicación, un shell integrado o aislado especial redistribuible y un programa de instalación. Para obtener más información acerca de la instalación y distribución, consulte [distribuir las aplicaciones de Shell aislado](distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  El [contrato de licencia de usuario final (CLUF)](https://www.visualstudio.com/en-us/support/legal/mt171552) para Visual Studio integrado y aislado shells incluye una sección en la recopilación de datos (**sección 3. Datos**).  Describe los datos de uso de cliente que pueden recopilarse por Microsoft de los usuarios de que el software de shell integrado o aisladas que se genera en la aplicación. Para obtener más información, consulte [Microsoft Visual Studio producto familia Privacy Statement](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Si recopila datos de uso independiente de los clientes a través de la aplicación, debe proporcionar aviso adecuado a los usuarios de la aplicación de lo que recopilan.  Cuando se distribuye el software de shell aislado o integrado como parte de la aplicación, según la licencia del Kit de desarrollo de Software de Visual Studio, debe incluir uno de los siguientes:  
>   
>  -   el contrato de licencia de usuario final como parte de su licencia de aplicación  
> -   sus propios términos de licencia que requiere que los clientes que acepten los términos que protegen el Visual Studio integran o aislada shell al menos tanta como los términos de licencia de usuario final de Microsoft para el software de shell  
  
## <a name="additional-resources"></a>Recursos adicionales  
 Para obtener más información acerca de los paquetes redistribuibles, consulte el [descargas de extensibilidad de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) sitio Web.  
  
## <a name="see-also"></a>Vea también  
 [Suministro de extensiones de Visual Studio](../shipping-visual-studio-extensions.md)