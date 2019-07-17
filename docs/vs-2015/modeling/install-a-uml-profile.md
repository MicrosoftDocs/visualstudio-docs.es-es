---
title: Instalar un perfil UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0187f7dede25900cdf3a78fdbfe2899e5f318472
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181498"
---
# <a name="install-a-uml-profile"></a>Instalar un perfil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender Visual Studio con un perfil UML. Un perfil permite agregar estereotipos y otras propiedades a los elementos que se pueden crear en los modelos UML. Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Si recibe un modelo UML que se haya creado con perfiles, algunas propiedades no se mostrarán a menos que instale los mismos perfiles.  
  
 Los perfiles se distribuyen dentro de una extensión de Visual Studio. Una extensión también puede contener otras características, como comandos de menú. Para obtener más información, consulte [administrar extensiones de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160728).  
  
### <a name="to-install-a-uml-profile-on-your-computer"></a>Para instalar un perfil UML en el equipo  
  
1. Se le debe haber proporcionado el perfil en forma de un archivo de extensión de Visual Studio (`.vsix`). Puede haber otras características en el mismo archivo.  
  
     Mueva el archivo `.vsix` a una ubicación adecuada en el equipo.  
  
2. En el Explorador de Windows (o Explorador de archivos) haga doble clic en el archivo `.vsix` o ábralo en [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
3. Haga clic en **instalar** en el cuadro de diálogo que aparece.  
  
4. Para desinstalar o deshabilitar temporalmente la extensión, abra **Administrador de extensiones** desde el **herramientas** menú.  
  
### <a name="to-uninstall-or-disable-a-profile-extension"></a>Para desinstalar o deshabilitar una extensión de perfil  
  
1. En Visual Studio **herramientas** menú, haga clic en **Administrador de extensiones**.  
  
2. Haga clic en la extensión que desea quitar y, a continuación, haga clic en **deshabilitar** o **desinstalar**.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md)
