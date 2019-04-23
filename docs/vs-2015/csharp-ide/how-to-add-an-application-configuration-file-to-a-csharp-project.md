---
title: Procedimiento Agregue un archivo de configuración de aplicación a un proyecto de C# | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c85690b34f0db705fe2a17e2f98d5b4f11433b3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044981"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedimiento Agregue un archivo de configuración de aplicación a un proyecto de C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al agregar un archivo de configuración de la aplicación (archivo app.config) a un proyecto de C#, puede personalizar el modo en que Common Language Runtime busca y carga archivos de ensamblado. Para obtener más información acerca de los archivos de configuración de aplicación, consulte [How the Runtime Locates Assemblies](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  No es compatible con el Store Windows <xref:System.Configuration>. Como resultado, las aplicaciones de Store no contienen una plantilla de app.config.  
  
 Al compilar el proyecto, el entorno de desarrollo copia automáticamente el archivo app.config, cambia el nombre de archivo de la copia para que coincida con el archivo ejecutable y, a continuación, mueve la copia en el directorio bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Para agregar un archivo de configuración para el proyecto de C#  
  
1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2. Expanda **instalado**, expanda **elementos de Visual C#** y, a continuación, elija el **archivo de configuración de aplicación** plantilla.  
  
3. En el cuadro de texto **Nombre**, escriba un nombre y, después, elija el botón **Agregar**.  
  
     Se agrega un archivo denominado app.config al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Administrar la configuración de la aplicación (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Esquema de los archivos de configuración](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Configurar aplicaciones](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Cómo: Configurar una aplicación para una versión de .NET Framework de destino](http://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Usar el entorno de desarrollo de Visual C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)