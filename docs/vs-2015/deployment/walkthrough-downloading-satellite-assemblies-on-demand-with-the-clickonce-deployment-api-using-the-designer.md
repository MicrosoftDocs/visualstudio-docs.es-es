---
title: 'Tutorial: Descargar ensamblados satélite a petición con la API mediante el Diseñador de implementación de ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8ed393a17c3489e0133a4a6534deb8f2dab1e428
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582768"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: descargar ensamblados satélite a petición con la implementación de ClickOnce API mediante el diseñador](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).  
  
Las aplicaciones de Windows Forms pueden configurarse para varias referencias culturales utilizando ensamblados satélite. Un *ensamblado satélite* es un ensamblado que contiene los recursos de aplicación para una referencia cultural que no sea la referencia cultural predeterminada de la aplicación.  
  
 Como se describe en [localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md), puede incluir varios ensamblados satélite para varias referencias culturales en el mismo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] descargará todos los ensamblados satélite en su implementación en el equipo cliente, aunque un cliente individual probablemente solo requiera un único ensamblado satélite.  
  
 En este tutorial se demuestra cómo marcar los ensamblados satélite como opcionales y descargar únicamente el ensamblado que necesite un equipo cliente para la configuración de su referencia cultural actual.  
  
> [!NOTE]
>  Con fines de prueba, los siguientes ejemplos de código establecen la referencia cultural en `ja-JP` mediante programación. Vea la sección “Pasos siguientes“ más adelante en este tema para obtener información sobre cómo ajustar este código para un entorno de producción.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>Para marcar los ensamblados satélite como opcionales  
  
1.  Compilar el proyecto. Esto generará los ensamblados satélite para todas las referencias culturales a las que vaya a realizar la localización.  
  
2.  Haga doble clic en el nombre del proyecto en el Explorador de soluciones y haga clic en **propiedades**.  
  
3.  Haga clic en el **publicar** pestaña y, a continuación, haga clic en **archivos de la aplicación**.  
  
4.  Seleccione el **mostrar todos los archivos** casilla de verificación para mostrar los ensamblados satélite. De forma predeterminada, todos los ensamblados satélite se incluirán en la implementación y estarán visibles en este cuadro de diálogo.  
  
     Un ensamblado satélite tendrá un nombre en el formulario *isoCode*\ApplicationName.resources.dll, donde *isoCode* es un identificador de idioma en formato RFC 1766.  
  
5.  Haga clic en **nuevo...**  en el **grupo de descarga** lista para cada identificador de idioma. Cuando se le pida un nombre de grupo de descarga, escriba el identificador de idioma. Por ejemplo, para un ensamblado satélite japonés, especificaría el nombre del grupo de descarga `ja-JP`.  
  
6.  Cerrar la **archivos de la aplicación** cuadro de diálogo.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Para descargar ensamblados satélite a petición en C#  
  
1.  Abra el archivo Program.cs. Si no ve este archivo en el Explorador de soluciones, seleccione el proyecto y en el **proyecto** menú, haga clic en **mostrar todos los archivos**.  
  
2.  Utilice el código siguiente para descargar el ensamblado satélite adecuado e iniciar la aplicación.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs#1)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Para descargar ensamblados satélite a petición en Visual Basic  
  
1.  En el **propiedades** ventana de la aplicación, haga clic en el **aplicación** ficha.  
  
2.  En la parte inferior de la página de ficha, haga clic en **ver eventos de aplicación**.  
  
3.  Agregue las siguientes importaciones al principio del archivo ApplicationEvents.VB.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#1)]  
  
4.  Agregue el código siguiente a la clase `MyApplication`.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#2)]  
  
## <a name="next-steps"></a>Pasos siguientes  
 En un entorno de producción, probablemente tenga que quitar la línea en los ejemplos de código que establece <xref:System.Threading.Thread.CurrentUICulture%2A> en un valor específico, porque los equipos cliente tendrán el valor correcto establecido de forma predeterminada. Cuando la aplicación se ejecute en un equipo cliente japonés, por ejemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` de forma predeterminada. Establecerlo mediante programación es una buena manera de probar los ensamblados satélite antes de implementar la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md)



