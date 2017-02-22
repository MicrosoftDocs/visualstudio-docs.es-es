---
title: "Tutorial: Descargar ensamblados sat&#233;lite a petici&#243;n con la API de implementaci&#243;n de ClickOnce mediante el dise&#241;ador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, globalización"
  - "implementación ClickOnce, adaptación"
  - "ClickOnce, descarga a petición"
  - "adaptación, Windows Forms"
  - "tutoriales, adaptación"
  - "Windows Forms, globalización"
  - "Windows Forms, adaptación"
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Descargar ensamblados sat&#233;lite a petici&#243;n con la API de implementaci&#243;n de ClickOnce mediante el dise&#241;ador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las aplicaciones de Windows Forms pueden configurarse para varias referencias culturales utilizando ensamblados satélite.  Un *ensamblado satélite* es un ensamblado que contiene los recursos de aplicación para una referencia cultural que no sea la referencia cultural predeterminada de la aplicación.  
  
 Tal y como se describe en [Localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md), puede incluir varios ensamblados satélite para varias referencias culturales en la misma implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  De forma predeterminada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] descargará todos los ensamblados satélite en su implementación en el equipo cliente, aunque un cliente individual probablemente solo requiera un único ensamblado satélite.  
  
 En este tutorial se demuestra cómo marcar los ensamblados satélite como opcionales y descargar únicamente el ensamblado que necesite un equipo cliente para la configuración de su referencia cultural actual.  
  
> [!NOTE]
>  Con fines de prueba, los siguientes ejemplos de código establecen la referencia cultural en `ja-JP` mediante programación.  Vea la sección “Pasos siguientes“ más adelante en este tema para obtener información sobre cómo ajustar este código para un entorno de producción.  
  
### Para marcar los ensamblados satélite como opcionales  
  
1.  Compilar el proyecto.  Esto generará los ensamblados satélite para todas las referencias culturales a las que vaya a realizar la localización.  
  
2.  Haga clic con el botón derecho en el nombre del proyecto en el Explorador de soluciones y, a continuación, haga clic en **Propiedades**.  
  
3.  Haga clic en la pestaña **Publicar** y, a continuación, haga clic en **Archivos de aplicación**.  
  
4.  Seleccione la casilla **Mostrar todos los archivos** para que se muestren los ensamblados satélite.  De forma predeterminada, todos los ensamblados satélite se incluirán en la implementación y estarán visibles en este cuadro de diálogo.  
  
     El nombre de los ensamblados satélite tiene la siguiente forma: *isoCode*\\ApplicationName.resources.dll, donde *isoCode* es un identificador de idioma en formato RFC 1766.  
  
5.  Haga clic en **Nuevo...** en la lista **Grupo de descarga** para cada identificador de idioma.  Cuando se le pida un nombre de grupo de descarga, escriba el identificador de idioma.  Por ejemplo, para un ensamblado satélite japonés, debe especificar el nombre de grupo de descarga `ja-JP`.  
  
6.  Cierre el cuadro de diálogo **Archivos de aplicación**.  
  
### Para descargar ensamblados satélite a petición en C\#  
  
1.  Abra el archivo Program.cs.  Si no ve este archivo en el Explorador de soluciones, seleccione el proyecto y en el menú **Proyecto** haga clic en **Mostrar todos los archivos**.  
  
2.  Utilice el código siguiente para descargar el ensamblado satélite adecuado e iniciar la aplicación.  
  
     [!code-cs[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### Para descargar ensamblados satélite a petición en Visual Basic  
  
1.  En la ventana **Propiedades** de la aplicación haga clic en la pestaña **Aplicación**.  
  
2.  En la parte inferior de la ficha, haga clic en **Ver eventos de aplicaciones**.  
  
3.  Agregue las siguientes importaciones al principio del archivo ApplicationEvents.VB.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Agregue el código siguiente a la clase `MyApplication`.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## Pasos siguientes  
 En un entorno de producción, probablemente tenga que quitar la línea en los ejemplos de código que establece <xref:System.Threading.Thread.CurrentUICulture%2A> en un valor específico, porque los equipos cliente tendrán el valor correcto establecido de forma predeterminada.  Cuando la aplicación se ejecute en un equipo cliente japonés, por ejemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` de forma predeterminada.  Establecerlo mediante programación es una buena manera de probar los ensamblados satélite antes de implementar la aplicación.  
  
## Vea también  
 [Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localizar aplicaciones ClickOnce](../deployment/localizing-clickonce-applications.md)