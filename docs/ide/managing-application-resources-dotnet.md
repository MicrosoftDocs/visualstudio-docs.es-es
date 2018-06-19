---
title: Administrar los recursos de la aplicación (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50825ea0d610625c69955deea1599206053fb889
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32064615"
---
# <a name="manage-application-resources-net"></a>Administrar los recursos de la aplicación (.NET)

Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.

Para obtener más información sobre los recursos de las aplicaciones de escritorio de .NET, vea [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Trabajar con recursos

En un proyecto de código administrado, abra la ventana de propiedades del proyecto. Puede abrir la ventana Propiedades de cualquiera de estas maneras:

- Hacer clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones** y seleccionar **Propiedades**.
- Escribir "propiedades del proyecto" en la ventana **Inicio rápido**.
- Presionar **Alt**+**Entrar** en la ventana **Explorador de soluciones**.

Seleccione la pestaña **Recursos** . Puede agregar un archivo *.resx* si el proyecto no contiene ninguno y luego agregar y eliminar diferentes tipos de recursos y modificar recursos existentes.

## <a name="resources-in-other-project-types"></a>Recursos en otros tipos de proyecto

Los recursos se administran de manera diferente en los proyectos de .NET que en otros tipos de proyecto. Para obtener más información sobre los recursos en:

- Aplicaciones de la Plataforma universal de Windows (UWP), vea [Recursos de aplicaciones y sistema de administración de recursos](/windows/uwp/app-resources/)
- Proyectos de C++, vea [Working with Resource Files](/cpp/windows/working-with-resource-files) (Trabajo con archivos de recursos) y [How to: Create a Resource](/cpp/windows/how-to-create-a-resource) (Cómo: Crear un recurso)

## <a name="see-also"></a>Vea también

- [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index)
