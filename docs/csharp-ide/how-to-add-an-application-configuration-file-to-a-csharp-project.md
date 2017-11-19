---
title: "Cómo: agregar un archivo de configuración de aplicación a un proyecto de C# | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Cómo: Agregar un archivo de configuración de aplicaciones a un proyecto de C#
Al agregar un archivo de configuración de aplicación (archivo app.config) a un proyecto de C#, puede personalizar cómo common language runtime busca y carga archivos de ensamblado. Para obtener más información acerca de los archivos de configuración de aplicación, consulte [cómo el tiempo de ejecución ubica ensamblados](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Las aplicaciones UWP no contiene una plantilla de app.config.
  
 Cuando se compila el proyecto, el entorno de desarrollo copia automáticamente el archivo app.config, cambia el nombre de archivo de la copia para que coincida con el archivo ejecutable y, a continuación, mueve la copia en el directorio bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Para agregar un archivo de configuración de aplicación al proyecto de C#  
  
1.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  Expanda **instalado**, expanda **elementos de Visual C#**y, a continuación, elija la **archivo de configuración de aplicación** plantilla.  
  
3.  En el **nombre** cuadro de texto, escriba un nombre y, a continuación, elija la **agregar** botón.  
  
     Un archivo denominado app.config se agrega al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Administrar la configuración de la aplicación (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Esquema de los archivos de configuración](/dotnet/framework/configure-apps/file-schema/index)   
 [Configurar aplicaciones](/dotnet/framework/configure-apps/index)   
 [Cómo: configurar una aplicación que tenga como destino una versión de .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Usar el entorno de desarrollo de Visual C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)