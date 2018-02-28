---
title: "Cómo: personalizar una característica de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: adb4283a56715da704df8991543ea89c6cbc79a4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Cómo: Personalizar una característica de SharePoint
  Puede crear y personalizar las características de SharePoint mediante el Diseñador de características de Visual Studio. Por ejemplo, puede establecer el ámbito de característica y agregar otras características como dependencias. De forma predeterminada, se abre el Diseñador de características cuando se agrega una nueva característica en el Explorador de soluciones o el Explorador de paquetes de SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Abrir el Diseñador de características  
 Puede agregar o quitar elementos de proyecto de SharePoint a una característica utilizando el Diseñador de características.  
  
#### <a name="to-open-the-feature-designer"></a>Para abrir el Diseñador de características  
  
1.  En **el Explorador de soluciones**, expanda **características**.  
  
2.  Haga doble clic en el *Feature1* de elemento o abra el menú contextual para el *Feature1* de elemento y, a continuación, elija **Diseñador de vistas**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Ver el archivo de manifiesto empaquetado  
 Puede utilizar el Diseñador de características para modificar y generar el archivo de manifiesto empaquetado para la característica (feature.xml). A continuación, puede ver el código XML de este archivo en Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Para ver el archivo de manifiesto empaquetado  
  
1.  En el **Diseñador de características**, elija la **manifiesto** ficha.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante el Explorador de soluciones  
  
1.  En **el Explorador de soluciones**, elija la **mostrar todos los archivos** icono.  
  
2.  Expanda características, expanda NombreCaracterística, expanda FeatureName.feature y, a continuación, abra el *NombreCaracterística*. Archivo Template.Xml.  
  
    > [!NOTE]  
    >  Cuando se abre el archivo de XML de manifiesto de plantilla de función, los archivos se validan automáticamente y pueden hacer caso omiso de las advertencias que aparecen en la ventana Lista de errores.  
  
## <a name="changing-the-manifest-template"></a>Cambiar la plantilla de manifiesto  
 Puede cambiar el código XML para el archivo de manifiesto de características en el Editor XML de Visual Studio o en el panel de la plantilla de manifiesto. Los cambios en el código XML se combina en el archivo de manifiesto empaquetado para la característica. Por ejemplo, puede que desee cambiar la plantilla de manifiesto para personalizar una propiedad de la característica.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto utilizando el Editor XML  
  
1.  En el **Diseñador de características**, elija la **manifiesto** , expanda la **Editar opciones** nodo y, a continuación, elija la **abierto en el Editor de XML** vínculo.  
  
     Cambios en el código XML se combinan en el archivo de manifiesto empaquetado.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto utilizando el recuadro plantilla de manifiesto  
  
1.  En el **Diseñador de características**, elija la **manifiesto** , expanda la **Editar opciones** nodo y, a continuación, cambie el código XML que aparece en el panel de la plantilla de manifiesto.  
  
     Los cambios en el XML aparecen en la **vista previa del manifiesto empaquetado** panel.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Sobrescribiendo el archivo de manifiesto empaquetado  
 Puede deshabilitar al diseñador de características y crear el archivo feature.xml manualmente. La primera vez que lleva a cabo este procedimiento, la configuración actual en el Diseñador de características se guarda en el archivo XML de plantilla de función. A continuación, puede modificar o sobrescribir el código XML.  
  
> [!NOTE]  
>  Si agrega o quita elementos de proyecto de SharePoint en el archivo XML mientras está deshabilitado el Diseñador de características, estos elementos de proyecto no se empaquetarán.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador  
  
1.  En el **Diseñador de características**, elija la **manifiesto** ficha.  
  
2.  Expanda el **Editar opciones** nodo, elija la **sobrescribir generado XML y editar el manifiesto en el editor XML** vincular y, a continuación, elija la **Sí** botón.  
  
     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.  
  
## <a name="enabling-the-feature-designer"></a>Habilitar al diseñador de características  
 Puede volver a habilitar el Diseñador de características para personalizar el archivo feature.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador  
  
1.  En el **Diseñador de características**, elija la **descarte manifiestos modificaciones y volver a habilitar el diseñador** vincular y, a continuación, elija la **Sí** botón.  
  
2.  La plantilla se actualiza con el texto original y se perderán los cambios realizados en el código XML.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  