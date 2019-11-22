---
title: Install a UML profile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14911cda4cfc2be5fece6005a879427c10529bbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298907"
---
# <a name="install-a-uml-profile"></a>Instalar un perfil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender Visual Studio con un perfil UML. Un perfil permite agregar estereotipos y otras propiedades a los elementos que se pueden crear en los modelos UML. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Si recibe un modelo UML que se haya creado con perfiles, algunas propiedades no se mostrarán a menos que instale los mismos perfiles.

 Los perfiles se distribuyen dentro de una extensión de Visual Studio. Una extensión también puede contener otras características, como comandos de menú. For more information, see [Managing Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160728).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Para instalar un perfil UML en el equipo

1. Se le debe haber proporcionado el perfil en forma de un archivo de extensión de Visual Studio (`.vsix`). Puede haber otras características en el mismo archivo.

     Mueva el archivo `.vsix` a una ubicación adecuada en el equipo.

2. En el Explorador de Windows (o Explorador de archivos) haga doble clic en el archivo `.vsix` o ábralo en [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Click **Install** in the dialog box that appears.

4. To uninstall or temporarily disable the extension, open **Extension Manager** from the **Tools** menu.

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Para desinstalar o deshabilitar una extensión de perfil

1. On the Visual Studio **Tools** menu, click **Extension Manager**.

2. Click the extension that you want to remove, and then click **Disable** or **Uninstall**.

## <a name="see-also"></a>Vea también
 [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md)
