---
title: Instalar un perfil UML | Microsoft Docs
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
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850664"
---
# <a name="install-a-uml-profile"></a>Instalar un perfil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender Visual Studio con un perfil UML. Un perfil permite agregar estereotipos y otras propiedades a los elementos que se pueden crear en los modelos UML. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Si recibe un modelo UML que se haya creado con perfiles, algunas propiedades no se mostrarán a menos que instale los mismos perfiles.

 Los perfiles se distribuyen dentro de una extensión de Visual Studio. Una extensión también puede contener otras características, como comandos de menú. Para obtener más información, consulte [Administración de extensiones de Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Para instalar un perfil UML en el equipo

1. Se le debe haber proporcionado el perfil en forma de un archivo de extensión de Visual Studio (`.vsix`). Puede haber otras características en el mismo archivo.

     Mueva el archivo `.vsix` a una ubicación adecuada en el equipo.

2. En el Explorador de Windows (o Explorador de archivos) haga doble clic en el archivo `.vsix` o ábralo en [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Haga clic en **instalar** en el cuadro de diálogo que aparece.

4. Para desinstalar o deshabilitar temporalmente la extensión, abra el **Administrador de extensiones** en el menú **herramientas** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Para desinstalar o deshabilitar una extensión de perfil

1. En el menú **herramientas** de Visual Studio, haga clic en **Administrador de extensiones**.

2. Haga clic en la extensión que desea quitar y, a continuación, haga clic en **deshabilitar** o **desinstalar**.

## <a name="see-also"></a>Vea también
 [Personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md)
