---
title: Administrar los recursos de la aplicación (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651384"
---
# <a name="managing-application-resources-net"></a>Administrar los recursos de la aplicación (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.

 Para más información sobre los recursos de aplicaciones de escritorio .NET, vea [Resources in Desktop Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Para más información sobre los recursos de aplicaciones de escritorio C++, vea [Working with Resource Files](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Las aplicaciones de la Tienda Windows usan un modelo de recursos distinto al de las aplicaciones de escritorio. Para obtener información sobre los recursos de las aplicaciones de la Tienda Windows, vea [Definición de recursos de aplicaciones](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) en el sitio web del Centro de desarrollo de Windows.

## <a name="working-with-resources"></a>Trabajar con recursos
 En un proyecto de código administrado, abra la ventana de propiedades del proyecto (haga clic en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Propiedades**o escriba las **propiedades del proyecto** en la ventana **Inicio rápido** , o bien presione ALT + ENTRAR en la ventana **Explorador de soluciones** ). Seleccione la pestaña **recursos** . Puede Agregar un archivo. resx si el proyecto no contiene uno ya, agregar y eliminar diferentes tipos de recursos y modificar los recursos existentes.

 Para obtener información sobre cómo trabajar con recursos en proyectos de C++, vea [How to: Create a Resource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
