---
title: "C&#243;mo: Agregar un archivo de configuraci&#243;n de aplicaciones a un proyecto de C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config (archivos), agregar a proyectos de C#"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C&#243;mo: Agregar un archivo de configuraci&#243;n de aplicaciones a un proyecto de C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Agrega un archivo de configuración de la aplicación \(archivo app.config\) a un proyecto de C\#, puede personalizar cómo Common Language Runtime busca y carga los archivos de ensamblado.  Para obtener más información sobre los archivos de configuración de la aplicación, vea [Cómo el motor en tiempo de ejecución ubica ensamblados](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  El almacén de Windows no admite <xref:System.Configuration>.  Como resultado, las aplicaciones almacenadas no contienen una plantilla app.config.  
  
 Al compilar el proyecto, el entorno de desarrollo copia automáticamente el archivo app.config, cambia el nombre de archivo de la copia para coincidir con la aplicación ejecutable, y luego mueve la copia en el directorio bin.  
  
### Para agregar un archivo de configuración de la aplicación al proyecto de C\#  
  
1.  En la barra de menú, elija **proyecto**, **agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  Expanda **Instalado**, expanda **Elementos de Visual C** y, a continuación la plantilla **Archivo de configuración de aplicaciones**.  
  
3.  En el cuadro de texto **Nombre**, escriba un nombre, y elija el botón **Add**.  
  
     Un archivo denominado app.config se agrega al proyecto.  
  
## Vea también  
 [Administrar la configuración de la aplicación \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Esquema de los archivos de configuración](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Configurar aplicaciones](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/es-es/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Utilizar el entorno de desarrollo de Visual C\#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)