---
title: "Shell (aislado o integrado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio"
  - "Shell de Visual Studio"
  - "Shell [Visual Studio]"
  - "Shell de Visual Studio, las aplicaciones basadas en shell"
  - "Shell [Visual Studio], aplicaciones de shell"
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Shell (aislado o integrado)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear su propia aplicación basada en Visual Studio en modo integrado o aislado. En el modo integrado, existen muchas características de Visual Studio además de la aplicación. En el modo aislado, debe elegir un subconjunto de características de Visual Studio que desea distribuir junto con su propia extensión.  
  
## Modo integrado  
 El modo integrado permite a los usuarios usar las características estándar de Visual Studio junto con las herramientas personalizadas. El shell integrado está pensado principalmente para el hospedaje de lenguajes de programación y herramientas de desarrollo de software.  
  
 Las herramientas personalizadas que se crean automáticamente en el shell integrado de mezcla con cualquier otra edición de Visual Studio está instalado en el mismo equipo. Puede proporcionar una versión redistribuible del shell integrado de Visual Studio si ya no está instalado Visual Studio.  
  
 La versión redistribuible del shell integrado de Visual Studio no incluye lenguajes de programación y las características que admitan sus respectivos sistemas de proyectos.  
  
> [!NOTE]
>  El modo integrado de shell de Visual Studio se puede instalar junto con todas las ediciones de Visual Studio excepto las ediciones Express.  
  
 Para obtener más información, consulta [Visual Studio Shell \(integrado\)](../extensibility/visual-studio-shell-integrated.md).  
  
## Modo de aislamiento  
 Modo aislado permite crear herramientas personalizadas que se ejecutan en paralelo con otras versiones de Visual Studio. Se pretende principalmente para las herramientas que pueden tener acceso a servicios de Visual Studio sin según todas las características estándar de Visual Studio. Puede personalizar la apariencia de las aplicaciones basadas en el shell aislado de Visual Studio. Puede desactivar fácilmente las características y los grupos de comandos de menú que no desea que aparezca junto con la aplicación.  
  
 Para obtener más información, consulta [Shell de aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## Distribuir la aplicación de Shell aislado o integrado  
 Para distribuir la aplicación de shell aislado o integrado, debe incluir la aplicación, un shell integrado o aislado especial redistribuible y un programa de instalación. Para obtener más información acerca de la instalación y distribución, consulte [Distribuir aplicaciones de Shell aislado](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  El [contrato de licencia de usuario final \(CLUF\)](https://www.visualstudio.com/en-us/support/legal/mt171552) para Visual Studio integrado y aislada shells incluye una sección sobre la recopilación de datos \(**sección 3. Data**\).  Describe los datos de uso de cliente pueden recopilados por Microsoft de los usuarios de que el software de shell integrado o aislado que se crean en la aplicación. Para obtener más información, consulte [Microsoft Visual Studio producto familia declaración](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Si recopila datos de uso independiente de sus clientes a través de la aplicación, debe proporcionar aviso adecuado a los usuarios de la aplicación de lo que se recopilan. Al distribuir el software de shell aislado o integrado como parte de la aplicación, según la licencia del Kit de desarrollo de Software de Visual Studio, debe incluir uno de los siguientes:  
>   
>  -   el contrato de licencia de usuario final como parte de su licencia de la aplicación  
> -   su propio CLUF que requiere que los clientes Aceptar los términos que protegen el Visual Studio integrado o aislado shell al menos tantos como los términos de licencia de usuario final de Microsoft para el software de shell  
  
## Recursos adicionales  
 Para obtener más información acerca de los paquetes redistribuibles, consulte el [descargas de extensibilidad de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) sitio Web.  
  
## Vea también  
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)