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
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2006f565edbca8a859cd2c155645e47e083b5528
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="managing-application-resources-net"></a>Administración de los recursos de aplicación (.NET)

Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.

Para más información sobre los recursos de aplicaciones de escritorio .NET, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Trabajo con recursos

En un proyecto de código administrado, abra la ventana de propiedades del proyecto. Puede abrir la ventana Propiedades de cualquiera de estas maneras:

- Hacer clic con el botón derecho en el nodo de proyecto del **Explorador de soluciones** y seleccionar **Propiedades**.
- Escribir "propiedades del proyecto" en la ventana **Inicio rápido**.
- Presionar **Alt**+**Entrar** en la ventana **Explorador de soluciones**.

Seleccione la pestaña **Recursos** . Puede agregar un archivo .resx si el proyecto no contiene uno ya y, a continuación, agregar y eliminar diferentes tipos de recursos y modificar los recursos existentes.

## <a name="resources-in-other-project-types"></a>Recursos en otros tipos de proyecto

Los recursos se administran de manera diferente en los proyectos de .NET que en otros tipos de proyecto. Para obtener más información sobre los recursos en:

- Aplicaciones de la Plataforma universal de Windows (UWP), vea [Recursos de aplicaciones y sistema de administración de recursos](/windows/uwp/app-resources/)
- Proyectos de C++, vea [Working with Resource Files](/cpp/windows/working-with-resource-files) (Trabajo con archivos de recursos) y [How to: Create a Resource](/cpp/windows/how-to-create-a-resource) (Procedimiento para crear un recurso)

## <a name="see-also"></a>Vea también

[Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index)