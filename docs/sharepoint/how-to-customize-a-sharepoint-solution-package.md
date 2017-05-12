---
title: "C&#243;mo: Personalizar un paquete de soluci&#243;n de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, paquetes"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Personalizar un paquete de soluci&#243;n de SharePoint
  Puede utilizar el diseñador de paquetes para crear y personalizar un paquete \(.wsp\).  Por ejemplo, puede agregar elementos y características de proyecto de SharePoint, especificar si se restablece el servidor web cuando se implementa la solución y establecer el tipo de servidor de implementación.  
  
## Abrir el diseñador de paquetes  
  
#### Para abrir el diseñador de paquetes  
  
-   En **Explorador de soluciones**, haga doble clic en **Paquete**, o elija **Diseñador de vistas** en el menú contextual para **Paquete**.  
  
## Ver el archivo de manifiesto empaquetado  
 Puede utilizar el diseñador de paquetes para modificar y generar el archivo de manifiesto empaquetado.  Después, puede ver el código XML de este archivo en Visual Studio.  
  
#### Para ver el archivo de origen XML  
  
1.  En **Diseñador de paquetes**, elija **Manifiesto**.  
  
#### Para ver el archivo de manifiesto empaquetado utilizando el Explorador de soluciones  
  
1.  En **Explorador de soluciones**, elija **Mostrar todos los archivos**.  
  
2.  Expanda el paquete, expanda Package.package, y abra el archivo Package.Template.xml.  
  
    > [!NOTE]  
    >  Al abrir el archivo XML de manifiesto de la plantilla de paquete, automáticamente se validan los archivos, y puede omitir las advertencias que aparecen en la ventana Lista de errores.  
  
## Cambiar la plantilla de manifiesto  
 Puede cambiar el código XML del archivo de manifiesto empaquetado en el Editor XML de Visual Studio o en el panel Plantilla de manifiesto.  Cualquier cambio en el código XML se combinan en el archivo de manifiesto empaquetado del paquete.  
  
#### Para cambiar la plantilla de manifiesto utilizando el editor XML  
  
1.  En **Diseñador de paquetes**, elija la ficha de **Manifiesto** , expanda el nodo de **Opciones de edición** , y elija el vínculo de **Abrir en editor XML** .  
  
     Los cambios efectuados en el XML se combinan en el archivo de manifiesto empaquetado.  
  
#### Para cambiar la plantilla de manifiesto utilizando el panel Plantilla de manifiesto  
  
1.  En **Diseñador de paquetes**, elija la ficha de **Manifiesto** , expanda el nodo de **Opciones de edición** , y después cambie el XML que aparece en el panel plantilla de manifiesto.  
  
     Los cambios efectuados en el XML aparecen en el panel **Vista previa del manifiesto empaquetado**.  
  
## Sobrescribir el archivo de manifiesto empaquetado  
 Puede deshabilitar el diseñador de paquetes y crear el archivo manifest.xml manualmente.  La primera vez que lleve a cabo este procedimiento, la configuración actual del diseñador de paquetes se guarda en el archivo XML de la plantilla del paquete.  Entonces puede modificar o sobrescribir el código XML.  
  
> [!NOTE]  
>  Si agrega o quita elementos y características de proyecto de SharePoint del archivo XML mientras está deshabilitado el diseñador de paquetes, estos elementos de proyecto y características no se empaquetarán.  
  
#### Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador  
  
1.  En **Diseñador de paquetes**, elija la ficha de **Manifiesto** .  
  
2.  .  
  
3.  Expanda el nodo de **Opciones de edición** , elija el vínculo de **Overwrite generó XML y edición de manifiestos en el Editor XML** , y después elija el botón de **Sí** .  
  
     La plantilla se actualiza con el archivo de manifiesto empaquetado.  
  
## Habilitar el diseñador de paquetes  
 Puede volver a habilitar el diseñador de paquetes para personalizar el archivo manifest.xml.  
  
#### Para habilitar de nuevo el diseñador  
  
1.  En **Diseñador de paquetes**, elija el vínculo de **Descartar las ediciones del manifiesto y vuelva a habilitar el diseñador** , y elija el botón de **Sí** .  
  
     La plantilla se actualiza con el texto original y se pierden los cambios efectuados en el XML.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  