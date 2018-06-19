---
title: Tipos de archivos de proyecto y solución
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947604"
---
# <a name="project-and-solution-file-types"></a>Tipos de archivos de proyecto y solución

Visual Studio admite muchos tipos de archivo. En una instalación concreta, los componentes instalados determinan los tipos de archivo compatibles. En este tema se incluyen los tipos de archivo de solución y proyecto compatibles en algunas instalaciones típicas.

## <a name="solution-files-sln-and-suo"></a>Archivos de solución (.sln y .suo)

En Visual Studio se usan dos tipos de archivo (.sln y .suo) para almacenar la configuración de las soluciones. Estos archivos, denominados colectivamente "archivos de solución", proporcionan al Explorador de soluciones la información que necesita para mostrar una interfaz gráfica para administrar los archivos.

|Comprobación de actualización|nombre|Description|
|---------------|----------|-----------------|
|.sln|Solución de Visual Studio|Organiza proyectos, elementos de proyecto y elementos de solución en la solución.|
|.suo|Opciones de usuario de la solución|Realiza el seguimiento de las personalizaciones de nivel de usuario que se han realizado en Visual Studio, como los puntos de interrupción.|

## <a name="project-files"></a>Archivos de proyecto

Los proyectos pueden contener muchos tipos de archivo diferentes. Por ejemplo, los archivos de código de C# tienen una extensión **.cs** y los de C++ tienen una extensión **.cpp**. Los recursos se almacenan en archivos **.resx** y el código XAML en archivos **.xaml**. Los archivos [app.config](../../ide/managing-application-settings-dotnet.md) contienen información de la aplicación que no se debe incluir en el código de la aplicación (como cadenas de conexión).

Para más información sobre los tipos de archivo en proyectos de C++, vea [Tipos de archivos creados para proyectos de Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Vea también

- [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)