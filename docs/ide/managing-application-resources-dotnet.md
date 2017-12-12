---
title: "Administrar los recursos de la aplicación (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Administrar los recursos de la aplicación (.NET)
Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.  
  
Para más información sobre los recursos de aplicaciones de escritorio .NET, vea [Resources in Desktop Apps](/dotnet/framework/resources/index). Para más información sobre los recursos de aplicaciones de escritorio C++, vea [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
Las aplicaciones de UWP usan un modelo de recursos distinto al de las aplicaciones de escritorio. Para obtener información sobre los recursos de las aplicaciones de Windows 8.x, consulte [Definición de recursos de una aplicación (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Trabajar con recursos  
En un proyecto de código administrado, abra la ventana de propiedades del proyecto. Puede abrir la ventana Propiedades de cualquiera de estas maneras:

- Hacer clic con el botón derecho en el nodo de proyecto del **Explorador de soluciones** y seleccionar **Propiedades**.
- Escribir **propiedades del proyecto** en la ventana **Inicio rápido**.
- Utilizar las teclas **Alt+Entrar** en la ventana del **Explorador de soluciones**.

Seleccione la pestaña **Recursos** . Puede agregar un archivo .resx si el proyecto no contiene uno ya y, a continuación, agregar y eliminar diferentes tipos de recursos y modificar los recursos existentes.  
  
Para obtener información sobre cómo trabajar con recursos en proyectos de C++, vea [How to: Create a Resource](/cpp/windows/how-to-create-a-resource).