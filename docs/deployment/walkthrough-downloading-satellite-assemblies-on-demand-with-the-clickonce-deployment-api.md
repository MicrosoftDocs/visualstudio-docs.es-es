---
title: 'Tutorial: Descargar ensamblados satélite a petición con la API de implementación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d7226726bc2eb9bbc53afa8920a26d342983af6
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281226"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce
Las aplicaciones de Windows Forms pueden configurarse para varias referencias culturales utilizando ensamblados satélite. Un *ensamblado satélite* es un ensamblado que contiene los recursos de aplicación para una referencia cultural que no sea la referencia cultural predeterminada de la aplicación.  
  
 Como se describe en [aplicaciones ClickOnce localizar](../deployment/localizing-clickonce-applications.md), puede incluir varios ensamblados satélite para varias referencias culturales en el mismo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] descargará todos los ensamblados satélite en su implementación en el equipo cliente, aunque un cliente individual probablemente solo requiera un único ensamblado satélite.  
  
 En este tutorial se demuestra cómo marcar los ensamblados satélite como opcionales y descargar únicamente el ensamblado que necesite un equipo cliente para la configuración de su referencia cultural actual. El siguiente procedimiento usa las herramientas disponibles en el [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. También puede realizar esta tarea mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consulte también [Tutorial: descargar ensamblados satélite a petición con la API mediante el Diseñador de implementación de ClickOnce](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) o [Tutorial: descargar ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
> [!NOTE]
>  Con fines de prueba, el siguiente ejemplo de código establece la referencia cultural en `ja-JP`mediante programación. Vea la sección “Pasos siguientes“ más adelante en este tema para obtener información sobre cómo ajustar este código para un entorno de producción.  
  
## <a name="prerequisites"></a>Requisitos previos  
 En este tema, se da por sentado que sabe agregar recursos localizados a la aplicación mediante Visual Studio. Para obtener instrucciones detalladas, consulte [Tutorial: formularios de Windows localizar](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Para descargar ensamblados satélite a petición  
  
1.  Agregue el siguiente código a la aplicación para habilitar la descarga a petición de ensamblados satélite.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Genere los ensamblados satélite para la aplicación mediante [Resgen.exe (Resource File Generator)](/dotnet/framework/tools/resgen-exe-resource-file-generator) o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Generar un manifiesto de aplicación o abra el manifiesto de aplicación existente, mediante el uso de *MageUI.exe*. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4.  Haga clic en la ficha **Archivos** .  
  
5.  Haga clic en el **puntos suspensivos** botón (**...** ) y seleccione el directorio que contiene todos los ensamblados y archivos, incluidos los ensamblados satélite generados mediante la aplicación *Resgen.exe*. (Un ensamblado satélite tendrá un nombre en el formulario  *\<isoCode > \ApplicationName.resources.dll*, donde \<isoCode > es un identificador de idioma en formato RFC 1766.)  
  
6.  Haga clic en **Rellenar** para agregar los archivos a la implementación.  
  
7.  Active la casilla **Opcional** de cada ensamblado satélite.  
  
8.  Establezca el campo de grupo de cada ensamblado satélite en su identificador de idioma ISO. Por ejemplo, para un ensamblado satélite japonés, debe especificar el nombre de grupo de descarga `ja-JP`. De este modo, se habilitará el código agregado en el paso 1 para descargar el ensamblado satélite adecuado, en función del valor de la propiedad <xref:System.Threading.Thread.CurrentUICulture%2A> del usuario.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En un entorno de producción, probablemente tenga que quitar la línea en el ejemplo de código que establece <xref:System.Threading.Thread.CurrentUICulture%2A> en un valor específico porque los equipos cliente tendrán establecido el valor correcto de forma predeterminada. Cuando la aplicación se ejecute en un equipo cliente japonés, por ejemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` de forma predeterminada. Establecer este valor mediante programación es una buena manera de probar los ensamblados satélite antes de implementar la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md)