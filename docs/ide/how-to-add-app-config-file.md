---
title: "Adición de un archivo app.config a un proyecto en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Cómo: Agregar un archivo de configuración de aplicaciones a un proyecto de C#

Al agregar un archivo de configuración de la aplicación (archivo app.config) a un proyecto de C#, puede personalizar el modo en que Common Language Runtime busca y carga archivos de ensamblado. Para obtener más información acerca de los archivos de configuración de la aplicación, consulte [Cómo el motor en tiempo de ejecución ubica ensamblados (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Las aplicaciones UWP no contienen un archivo app.config.

Cuando se compila el proyecto, el entorno de desarrollo copia automáticamente el archivo app.config, cambia el nombre de archivo de la copia para que coincida con el archivo ejecutable y, a continuación, mueve la copia al directorio **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Para agregar un archivo de configuración de la aplicación a un proyecto de C#

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

1. Expanda **Instalado** > **Elementos de Visual C#** y, a continuación, elija la plantilla **Archivo de configuración de aplicación**.

3. En el cuadro de texto **Nombre**, escriba un nombre y, después, elija el botón **Agregar**.

     A file named app.config is added to your project.

## <a name="see-also"></a>Vea también

[Administrar la configuración de la aplicación (.NET)](../ide/managing-application-settings-dotnet.md)  
[Esquema de los archivos de configuración de .NET Framework](/dotnet/framework/configure-apps/file-schema/index)  
[Configurar aplicaciones de .NET Framework](/dotnet/framework/configure-apps/index)