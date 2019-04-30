---
title: Procedimiento Personalizar una característica de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a00f3c58f917e7355a63ebca71c74127826a2e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429214"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Procedimiento Personalizar una característica de SharePoint
  Puede crear y personalizar las características de SharePoint mediante el Diseñador de características en Visual Studio. Por ejemplo, puede establecer el ámbito de característica y agregar otras características como dependencias. De forma predeterminada, se abre el Diseñador de características cuando se agrega una nueva característica en el Explorador de soluciones o el Explorador de paquetes de SharePoint.

## <a name="opening-the-feature-designer"></a>Abrir el Diseñador de características
 Puede agregar o quitar elementos de proyecto de SharePoint a una función mediante el Diseñador de características.

#### <a name="to-open-the-feature-designer"></a>Para abrir el Diseñador de características

1. En **el Explorador de soluciones**, expanda **características**.

2. Haga doble clic en el *Feature1* de elemento, o abra el menú contextual para el *Feature1* de elemento y, a continuación, elija **Diseñador de vistas**.

## <a name="view-the-packaged-manifest-file"></a>Ver el archivo de manifiesto empaquetado
 Puede usar el Diseñador de características para modificar y generar el archivo de manifiesto empaquetado para la característica (*feature.xml*). A continuación, puede ver el código XML de este archivo en Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Para ver el archivo de manifiesto empaquetado

1. En el **característica Diseñador**, elija el **manifiesto** ficha.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante el Explorador de soluciones

1. En **el Explorador de soluciones**, elija el **mostrar todos los archivos** icono.

2. Expanda las características, expanda FeatureName, expanda FeatureName.feature y, a continuación, abra el  *\<NombreDeCaracterística >. Template.XML* archivo.

    > [!NOTE]
    > Al abrir el archivo de XML de manifiesto de plantilla de función, los archivos se validan automáticamente y se pueden omitir las advertencias que aparecen en la ventana Lista de errores.

## <a name="change-the-manifest-template"></a>Cambiar la plantilla de manifiesto
 Puede cambiar el código XML para el archivo de manifiesto de característica en el Editor XML de Visual Studio o en el panel de la plantilla de manifiesto. Los cambios en el código XML se combina con el archivo de manifiesto empaquetado para la característica. Por ejemplo, desea cambiar la plantilla de manifiesto para personalizar una propiedad Feature.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto mediante el Editor XML

1. En el **característica Diseñador**, elija el **manifiesto** , expanda el **Editar opciones** nodo y, a continuación, elija el **abierto en el Editor XML** vínculo.

     Los cambios realizados en el código XML se combinan en el archivo de manifiesto empaquetado.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto mediante el panel de la plantilla de manifiesto

1. En el **característica Diseñador**, elija el **manifiesto** , expanda el **Editar opciones** nodo y, a continuación, cambie el código XML que aparece en el panel de la plantilla de manifiesto.

     Los cambios en el XML aparecen en la **vista previa del manifiesto empaquetado** panel.

## <a name="overwrite-the-packaged-manifest-file"></a>Sobrescribir el archivo de manifiesto empaquetado
 Puede deshabilitar el Diseñador de características y crear el *feature.xml* archivo manualmente. La primera vez que realice este procedimiento, la configuración actual en el Diseñador de características se guarda en el archivo XML de plantilla de función. A continuación, puede modificar o sobrescribir el código XML.

> [!NOTE]
> Si agrega o quita elementos de proyecto de SharePoint en el archivo XML mientras está deshabilitado el Diseñador de características, no se empaquetan estos elementos de proyecto.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador

1. En el **característica Diseñador**, elija el **manifiesto** ficha.

2. Expanda el **Editar opciones** nodo, elija el **sobrescritura generado XML y editar el manifiesto en el editor XML** vincular y, a continuación, elija el **Sí** botón.

     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.

## <a name="enable-the-feature-designer"></a>Habilitar al diseñador de características
 Puede volver a habilitar el Diseñador de características para personalizar el *feature.xml* archivo.

#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador

1. En el **característica Diseñador**, elija el **descarte manifiesto modificaciones y vuelva a habilitar el diseñador** vincular y, a continuación, elija el **Sí** botón.

2. La plantilla se actualiza con el texto original y se pierden los cambios realizados en el código XML.

## <a name="see-also"></a>Vea también
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
