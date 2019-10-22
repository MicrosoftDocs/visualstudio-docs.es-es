---
title: 'Cómo: agregar un archivo de configuración de aplicación a C# un proyecto | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667532"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Cómo: Agregar un archivo de configuración de aplicaciones a un proyecto de C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al agregar un archivo de configuración de la aplicación (archivo app.config) a un proyecto de C#, puede personalizar el modo en que Common Language Runtime busca y carga archivos de ensamblado. Para obtener más información sobre los archivos de configuración de la aplicación, vea [cómo el motor en tiempo de ejecución ubica ensamblados](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> La tienda Windows no es compatible con <xref:System.Configuration>. Como resultado, las aplicaciones de la tienda no contienen una plantilla app. config.

 Al compilar el proyecto, el entorno de desarrollo copia automáticamente el archivo app. config, cambia el nombre de archivo de la copia para que coincida con el ejecutable y, a continuación, mueve la copia al directorio bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Para agregar un archivo de configuración de la C# aplicación al proyecto

1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

2. Expanda **instalado**, **elementos C# visuales**y, a continuación, elija la plantilla **archivo de configuración** de la aplicación.

3. En el cuadro de texto **Nombre**, escriba un nombre y, después, elija el botón **Agregar**.

     Se agregará un archivo denominado app. config al proyecto.

## <a name="see-also"></a>Vea también
 Administración de la configuración de la [aplicación (.net) esquema del](../ide/managing-application-settings-dotnet.md) [archivo de configuración](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) configuración de [aplicaciones](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [Cómo: configurar una aplicación para que tenga como destino una versión de .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [mediante el entorno de desarrollo de Visual Studio para C# ](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)