---
title: Shell (aislado o integrado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850229"
---
# <a name="shell-isolated-or-integrated"></a>Shell (aislado o integrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear su propia aplicación basada en Visual Studio en modo integrado o aislado. En el modo integrado, muchas características de Visual Studio están disponibles además de la aplicación. En el modo aislado, puede elegir un subconjunto de características de Visual Studio que desea distribuir junto con su propia extensión.  
  
## <a name="integrated-mode"></a>Modo integrado  
 El modo integrado permite a los usuarios usar las características estándar de Visual Studio junto con las herramientas personalizadas. El shell integrado está diseñado principalmente para hospedar lenguajes de programación y herramientas de desarrollo de software.  
  
 Las herramientas personalizadas que se compilan en el shell integrado se fusionan automáticamente con cualquier otra edición de Visual Studio que esté instalada en el mismo equipo. Puede proporcionar una versión redistribuible del shell integrado de Visual Studio si aún no está instalado Visual Studio.  
  
 La versión redistribuible del shell integrado de Visual Studio no incluye los lenguajes de programación y las características que admiten sus sistemas de proyecto respectivos.  
  
> [!NOTE]
> El modo integrado de Visual Studio Shell se puede instalar junto con todas las ediciones de Visual Studio, excepto las ediciones Express.  
  
 Para obtener más información, vea [Visual Studio Shell (integrado)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo aislado  
 El modo aislado le permite crear herramientas personalizadas que se ejecutan en paralelo con otras versiones de Visual Studio. Está diseñado principalmente para las herramientas que pueden tener acceso a los servicios de Visual Studio sin depender de todas las características estándar de Visual Studio. Puede personalizar la apariencia de las aplicaciones compiladas en el shell aislado de Visual Studio. Puede desactivar fácilmente las características y los grupos de comandos de menú que no desea que aparezcan junto con la aplicación.  
  
 Para obtener más información, vea [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribución de la aplicación de Shell integrada o aislada  
 Para distribuir la aplicación de Shell integrada o aislada, debe incluir la aplicación, un paquete redistribuible de Shell integrado o aislado especial, y un programa de instalación. Para obtener más información acerca de la distribución e instalación, consulte [distribuir aplicaciones de Shell aislado](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> El [contrato de licencia para el usuario final (CLUF)](https://www.visualstudio.com/support/legal/mt171552) de los shells integrados y aislados de Visual Studio incluye una sección sobre la recopilación de datos (**sección 3). Datos**).  Describe los datos de uso del cliente que Microsoft puede recopilar de los usuarios del software de Shell integrado o aislado que se crea en la aplicación. Para obtener más información, vea [Microsoft Visual Studio declaración de privacidad](https://www.visualstudio.com/dn948229)de la familia de productos.  
> 
> Si recopila datos de uso independientes de sus clientes a través de la aplicación, debe proporcionar el aviso adecuado a los usuarios de la aplicación de lo que recopile.  Al distribuir el software de Shell aislado o integrado como parte de la aplicación, según la licencia del kit de desarrollo de software de Visual Studio, debe incluir una de las siguientes opciones:  
> 
> - el contrato de licencia para el usuario final como parte de la licencia de la aplicación  
> - su propio CLUF que requiere que los clientes acepten los términos que protegen el shell integrado o aislado de Visual Studio al menos tanto como los términos de licencia del usuario final de Microsoft para el software de Shell.  
  
## <a name="additional-resources"></a>Recursos adicionales  
 Para obtener más información acerca de los paquetes redistribuibles, vea el sitio web de [descargas de extensibilidad de Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="see-also"></a>Consulte también  
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
