---
title: "C&#243;mo: Personalizar una caracter&#237;stica de SharePoint | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, características"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# C&#243;mo: Personalizar una caracter&#237;stica de SharePoint
  Puede crear y personalizar las características de SharePoint utilizando el diseñador de características en Visual Studio.  Por ejemplo, puede establecer el ámbito Característica y agregar otras características como dependencias.  De forma predeterminada, se abre el diseñador de características cuando se agrega una nueva característica en el Explorador de soluciones o el Explorador de paquetes de SharePoint.  
  
## Abrir el Diseñador de características  
 Puede agregar o quitar los elementos de proyecto de SharePoint de una característica utilizando el diseñador de características.  
  
#### Para abrir el Diseñador de características  
  
1.  En el **Explorador de soluciones**, expanda **Características**.  
  
2.  Haga doble clic en el elemento de *Feature1* , o abra el menú contextual para el elemento de *Feature1* y elija **Diseñador de vistas**.  
  
## Ver el archivo de manifiesto empaquetado  
 Puede utilizar el diseñador de características para modificar y generar el archivo de manifiesto empaquetado para la característica \(feature.xml\).  Después, puede ver el código XML de este archivo en Visual Studio.  
  
#### Para ver el archivo de manifiesto empaquetado  
  
1.  En **Diseñador de características**, elija la ficha de **Manifiesto** .  
  
#### Para ver el archivo de manifiesto empaquetado utilizando el Explorador de soluciones  
  
1.  En **Explorador de soluciones**, elija el icono de **Mostrar todos los archivos** .  
  
2.  Expanda características, expanda FeatureName, expanda FeatureName.feature, abra *FeatureName*. Archivo de Template.xml.  
  
    > [!NOTE]  
    >  Al abrir el archivo XML de manifiesto de la plantilla de la característica, automáticamente se validan los archivos y se pueden omitir las advertencias que aparecen en la ventana Lista de errores.  
  
## Cambiar la plantilla de manifiesto  
 Puede cambiar el código XML del archivo de característica empaquetado en el Editor XML de Visual Studio o en el panel Plantilla de manifiesto.  Los cambios que se hagan en el código XML se combinan en el archivo de manifiesto empaquetado de la característica.  Por ejemplo, puede desear cambiar la plantilla de manifiesto para personalizar una propiedad de la característica.  
  
#### Para cambiar la plantilla de manifiesto utilizando el editor XML  
  
1.  En **Diseñador de características**, elija la ficha de **Manifiesto** , expanda el nodo de **Opciones de edición** , y elija el vínculo de **Abrir en editor XML** .  
  
     Los cambios efectuados en el XML se combinan en el archivo de manifiesto empaquetado.  
  
#### Para cambiar la plantilla de manifiesto utilizando el panel Plantilla de manifiesto  
  
1.  En **Diseñador de características**, elija la ficha de **Manifiesto** , expanda el nodo de **Opciones de edición** , y después cambie el XML que aparece en el panel plantilla de manifiesto.  
  
     Los cambios efectuados en el XML aparecen en el panel **Vista previa del manifiesto empaquetado**.  
  
## Sobrescribir el archivo de manifiesto empaquetado  
 Puede deshabilitar el diseñador de características y crear el archivo feature.xml manualmente.  La primera vez que lleve a cabo este procedimiento, la configuración actual del diseñador de características se guarda en el archivo XML de la plantilla de la característica.  Entonces puede modificar o sobrescribir el código XML.  
  
> [!NOTE]  
>  Si agrega o quita elementos de proyecto de SharePoint del archivo XML mientras está deshabilitado el diseñador de características, estos elementos no se empaquetarán.  
  
#### Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador  
  
1.  En **Diseñador de características**, elija la ficha de **Manifiesto** .  
  
2.  Expanda el nodo de **Opciones de edición** , elija el vínculo de **Overwrite generó XML y edición de manifiestos en el Editor XML** , y después elija el botón de **Sí** .  
  
     La plantilla se actualiza con el archivo de manifiesto empaquetado.  
  
## Habilitar el diseñador de características  
 Puede volver a habilitar el diseñador de características para personalizar el archivo feature.xml.  
  
#### Para habilitar de nuevo el diseñador  
  
1.  En **Diseñador de características**, elija el vínculo de **Descartar las ediciones del manifiesto y vuelva a habilitar el diseñador** , y elija el botón de **Sí** .  
  
2.  La plantilla se actualiza con el texto original y se pierden los cambios efectuados en el XML.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  