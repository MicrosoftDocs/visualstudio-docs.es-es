---
title: 'Cómo: personalizar una característica de SharePoint | Microsoft Docs'
description: Personalización de las características de SharePoint en Visual Studio. El diseñador de características se abre cuando se agrega una nueva característica en Explorador de soluciones o en el explorador de paquetes de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b4846d79af7a031970e8870626f88450e8a3e647
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903668"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Cómo: personalizar una característica de SharePoint
  Puede crear y personalizar las características de SharePoint mediante el diseñador de características de Visual Studio. Por ejemplo, puede establecer el ámbito de la característica y agregar otras características como dependencias. De forma predeterminada, el diseñador de características se abre cuando se agrega una nueva característica en Explorador de soluciones o en el explorador de paquetes de SharePoint.

## <a name="opening-the-feature-designer"></a>Abrir el diseñador de características
 Puede Agregar o quitar elementos de proyecto de SharePoint a una característica mediante el diseñador de características.

#### <a name="to-open-the-feature-designer"></a>Para abrir el diseñador de características

1. En **Explorador de soluciones**, expanda **características**.

2. Haga doble clic en el elemento *Feature1* o abra el menú contextual del elemento *Feature1* y, a continuación, elija **Diseñador de vistas**.

## <a name="view-the-packaged-manifest-file"></a>Ver el archivo de manifiesto empaquetado
 Puede usar el diseñador de características para modificar y generar el archivo de manifiesto empaquetado para la característica (*feature.xml*). Después, puede ver el código XML de este archivo en Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Para ver el archivo de manifiesto empaquetado

1. En el **Diseñador de características**, elija la pestaña **manifiesto** .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante Explorador de soluciones

1. En **Explorador de soluciones**, elija el icono **Mostrar todos los archivos** .

2. Expanda características, expanda FeatureName, expanda FeatureName. característica y, a continuación, abra el archivo de *\<FeatureName>.Template.xml* .

    > [!NOTE]
    > Al abrir el archivo XML de manifiesto de la plantilla de características, los archivos se validan automáticamente y se pueden omitir las advertencias que aparecen en la ventana de Lista de errores.

## <a name="change-the-manifest-template"></a>Cambiar la plantilla de manifiesto
 Puede cambiar el código XML del archivo de manifiesto de características en el editor XML de Visual Studio o en el panel de plantillas de manifiesto. Cualquier cambio en el código XML se combina en el archivo de manifiesto empaquetado de la característica. Por ejemplo, puede que desee cambiar la plantilla de manifiesto para personalizar una propiedad de característica.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto mediante el editor XML

1. En el **Diseñador de características**, elija la pestaña **manifiesto** , expanda el nodo **Opciones de edición** y, a continuación, elija el vínculo **abrir en el editor XML** .

     Los cambios en el XML se combinan en el archivo de manifiesto empaquetado.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto mediante el panel de plantillas de manifiesto

1. En el **Diseñador de características**, elija la pestaña **manifiesto** , expanda el nodo **Opciones de edición** y, a continuación, cambie el XML que aparece en el panel plantilla de manifiesto.

     Los cambios en el XML aparecen en el panel **vista previa del manifiesto empaquetado** .

## <a name="overwrite-the-packaged-manifest-file"></a>Sobrescribir el archivo de manifiesto empaquetado
 Puede deshabilitar el diseñador de características y crear el archivo de *feature.xml* manualmente. La primera vez que realice este procedimiento, la configuración actual en el diseñador de características se guarda en el archivo XML de la plantilla de características. A continuación, puede modificar o sobrescribir el código XML.

> [!NOTE]
> Si agrega o quita elementos de proyecto de SharePoint en el archivo XML mientras el diseñador de características está deshabilitado, estos elementos de proyecto no se empaquetan.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador

1. En el **Diseñador de características**, elija la pestaña **manifiesto** .

2. Expanda el nodo **Opciones de edición** , elija el vínculo **sobrescribir XML generado y editar manifiesto en el editor XML** y, a continuación, elija el botón **sí** .

     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.

## <a name="enable-the-feature-designer"></a>Habilitar el diseñador de características
 Puede volver a habilitar el diseñador de características para personalizar el archivo de *feature.xml* .

#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador

1. En el **Diseñador de características**, elija el vínculo **descartar cambios de manifiesto y volver a habilitar el diseñador** y, a continuación, elija el botón **sí** .

2. La plantilla se actualiza con el texto original y se pierden los cambios en el XML.

## <a name="see-also"></a>Consulte también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
