---
title: Introducción a aplicaciones internacionales basadas en .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ca63ead6b2014dfe0d90d496ef4b7d7efe7f63
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54784805"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Introducción a aplicaciones internacionales basadas en .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hay dos partes para crear una aplicación de uso internacional: globalización, que es el proceso de diseñar aplicaciones que puedan adaptarse a distintas referencias culturales, y la localización, que es el proceso de traducir los recursos para una referencia cultural concreta. Para obtener información general sobre el diseño de aplicaciones para un público internacional, consulte [Prácticas recomendadas para desarrollar aplicaciones de uso internacional](http://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 El modelo de localización de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] consta de un ensamblado principal que contiene el código de aplicación y los recursos de reserva (cadenas, imágenes y otros objetos del lenguaje en que se ha programado originalmente la aplicación). Cada aplicación localizada tendrá ensamblados satélite o ensamblados que contienen solo los recursos localizados. Dado que el ensamblado principal contiene siempre los recursos de reserva, si un recurso no se encuentra en el ensamblado satélite localizado, el <xref:System.Resources.ResourceManager> intentará cargarlo de forma jerárquica y usará finalmente el recurso de reserva del ensamblado principal. El sistema de reserva de recursos se explica con mayor detalle en [Organización jerárquica de recursos para la localización](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Un recurso de localización que debería usar es el glosario de todos los productos localizados de Microsoft. Este archivo CSV contiene más de 12.000 términos en inglés y las traducciones de los términos en hasta 59 idiomas diferentes. El glosario está disponible para su descarga en la página web [Microsoft Terminology Translations](http://go.microsoft.com/fwlink/?LinkId=128146) (Traducciones de terminología de Microsoft).  
  
 El sistema de proyectos para aplicaciones de Windows Forms puede generar archivos de recursos para el recurso de reserva y para todos los idiomas de interfaz de usuario adicionales que quiera. El archivo de recursos de reserva se compila en el ensamblado principal y los archivos de recursos específicos de la referencia cultural se compilan después en ensamblados satélite, uno para cada idioma de interfaz de usuario. Al compilar un proyecto, los archivos de recursos se compilan desde el formato XML de Visual Studio (.resx) en un formato binario intermedio (.resources), que se inserta después en ensamblados satélite.  
  
 El sistema del proyecto de Windows Forms y formularios Web Forms le permite compilar archivos de recursos mediante una plantilla de archivo de recursos de ensamblado, acceder a los recursos y compilar el proyecto. Los ensamblados satélite se crearán junto con el ensamblado principal.  
  
 Cuando se ejecuta una aplicación localizada, dos valores de referencia cultural determinan su apariencia. (Una *referencia cultural* es un conjunto de información de preferencia del usuario relacionada con el idioma, el entorno y las convenciones culturales del usuario). La configuración del idioma de interfaz de usuario determina qué recursos se cargarán. El idioma de interfaz de usuario se establece como `UICulture` en las directivas de página y los archivos Web.config y como <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> en el código de Visual Basic o Visual C#. La configuración de referencia cultural determina el formato de valores como fechas, números, moneda, etc. La referencia cultural se establece como `Culture` en las directivas de página y los archivos Web.config, <xref:System.Globalization.CultureInfo.CurrentCulture%2A> en el código de Visual Basic o Visual C#.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)   
 [Seguridad y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md)
