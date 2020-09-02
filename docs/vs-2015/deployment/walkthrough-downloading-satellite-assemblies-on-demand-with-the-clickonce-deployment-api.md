---
title: 'Tutorial: descargar ensamblados satélite a petición con la API de implementación de ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686351"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las aplicaciones de Windows Forms pueden configurarse para varias referencias culturales utilizando ensamblados satélite. Un *ensamblado satélite* es un ensamblado que contiene los recursos de aplicación para una referencia cultural que no sea la referencia cultural predeterminada de la aplicación.  
  
 Como se describe en [localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md), puede incluir varios ensamblados satélite para varias referencias culturales en la misma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] descargará todos los ensamblados satélite en su implementación en el equipo cliente, aunque un cliente individual probablemente solo requiera un único ensamblado satélite.  
  
 En este tutorial se demuestra cómo marcar los ensamblados satélite como opcionales y descargar únicamente el ensamblado que necesite un equipo cliente para la configuración de su referencia cultural actual. El siguiente procedimiento usa las herramientas disponibles en el [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. También puede realizar esta tarea mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  Consulte también los tutoriales sobre [descarga de ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) o [descarga de ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
> Con fines de prueba, el siguiente ejemplo de código establece la referencia cultural en `ja-JP`mediante programación. Vea la sección “Pasos siguientes“ más adelante en este tema para obtener información sobre cómo ajustar este código para un entorno de producción.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 En este tema, se da por sentado que sabe agregar recursos localizados a la aplicación mediante Visual Studio. Para obtener instrucciones detalladas, vea [Tutorial: Adaptar Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Para descargar ensamblados satélite a petición  
  
1. Agregue el siguiente código a la aplicación para habilitar la descarga a petición de ensamblados satélite.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. Genere los ensamblados satélite de la aplicación mediante [Resgen.exe (generador de archivos de recursos)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. Genere un manifiesto de aplicación o abra el manifiesto de aplicación existente mediante MageUI.exe. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4. Haga clic en la ficha **Archivos** .  
  
5. Haga clic en el botón de **puntos suspensivos** (**...**) y seleccione el directorio que contiene todos los archivos y ensamblados de la aplicación, incluidos los ensamblados satélite generados mediante Resgen.exe. (Un ensamblado satélite tendrá un nombre con el formato *isoCode*\ApplicationName.resources.dll, donde *isoCode* es un identificador de idioma en formato RFC 1766).  
  
6. Haga clic en **Rellenar** para agregar los archivos a la implementación.  
  
7. Active la casilla **Opcional** de cada ensamblado satélite.  
  
8. Establezca el campo de grupo de cada ensamblado satélite en su identificador de idioma ISO. Por ejemplo, para un ensamblado satélite japonés, debe especificar el nombre de grupo de descarga `ja-JP`. De este modo, se habilitará el código agregado en el paso 1 para descargar el ensamblado satélite adecuado, en función del valor de la propiedad <xref:System.Threading.Thread.CurrentUICulture%2A> del usuario.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En un entorno de producción, probablemente tenga que quitar la línea en el ejemplo de código que establece <xref:System.Threading.Thread.CurrentUICulture%2A> en un valor específico porque los equipos cliente tendrán establecido el valor correcto de forma predeterminada. Cuando la aplicación se ejecute en un equipo cliente japonés, por ejemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` de forma predeterminada. Establecer este valor mediante programación es una buena manera de probar los ensamblados satélite antes de implementar la aplicación.  
  
## <a name="see-also"></a>Consulte también  
 [Localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md)
