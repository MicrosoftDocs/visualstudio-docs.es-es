---
title: 'Cómo: personalizar un paquete de solución de SharePoint | Microsoft Docs'
description: Use el diseñador de paquetes para crear y personalizar un paquete de solución de SharePoint (. wsp). Permite ver o sobrescribir el archivo de manifiesto empaquetado. Cambie la plantilla de manifiesto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 149e99a3ba86f1eec22d90618abfd8972ed68e97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959901"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Cómo: personalizar un paquete de solución de SharePoint
  Puede usar el diseñador de paquetes para crear y personalizar un paquete (*. wsp*). Por ejemplo, puede agregar características y elementos de proyecto de SharePoint, especificar si el servidor Web se restablece cuando se implementa la solución y establecer el tipo de servidor de implementación.

## <a name="open-the-package-designer"></a>Abrir el diseñador de paquetes

#### <a name="to-open-the-package-designer"></a>Para abrir el diseñador de paquetes

- En **Explorador de soluciones**, haga doble clic en **Paquete** o elija **Ver diseñador** en el menú contextual del **paquete**.

## <a name="view-the-packaged-manifestffile"></a>Ver el manifestfFile empaquetado
 Puede usar el diseñador de paquetes para modificar y generar el archivo de manifiesto empaquetado. Después, puede ver el código XML de este archivo en Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Para ver el archivo de origen XML

1. En el **Diseñador de paquetes**, elija **manifiesto**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante Explorador de soluciones

1. En el **Explorador de soluciones**, elija **Mostrar todos los archivos**.

2. Expanda paquete, expanda paquete. paquete y, a continuación, abra el archivo de *Package.Template.xml* .

    > [!NOTE]
    > Al abrir el archivo XML de manifiesto para la plantilla de paquete, los archivos se validan automáticamente y puede omitir las advertencias que aparecen en la ventana Lista de errores.

## <a name="change-the-manifest-template"></a>Cambiar la plantilla de manifiesto
 Puede cambiar el código XML del archivo de manifiesto empaquetado en el editor XML de Visual Studio o en el panel de plantillas de manifiesto. Cualquier cambio en el código XML se combina en el archivo de manifiesto empaquetado para el paquete.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto mediante el editor XML

1. En el **Diseñador de paquetes**, elija la pestaña **manifiesto** , expanda el nodo **Opciones de edición** y, a continuación, elija el vínculo **abrir en el editor XML** .

     Los cambios en el XML se combinan en el archivo de manifiesto empaquetado.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto mediante el panel de plantillas de manifiesto

1. En el **Diseñador de paquetes**, elija la pestaña **manifiesto** , expanda el nodo **Opciones de edición** y, a continuación, cambie el XML que aparece en el panel plantilla de manifiesto.

     Los cambios en el XML aparecen en el panel **vista previa del manifiesto empaquetado** .

## <a name="overwrite-the-packaged-manifest-file"></a>Sobrescribir el archivo de manifiesto empaquetado
 Puede deshabilitar el diseñador de paquetes y crear el archivo de *manifest.xml* manualmente. La primera vez que realice este procedimiento, la configuración actual del diseñador de paquetes se guarda en el archivo XML de la plantilla de paquete. A continuación, puede modificar o sobrescribir el código XML.

> [!NOTE]
> Si agrega o quita elementos y características de proyecto de SharePoint en el archivo XML mientras el diseñador de paquetes está deshabilitado, estos elementos de proyecto y características no se empaquetan.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador

1. En el **Diseñador de paquetes**, elija la pestaña **manifiesto** .

2. Expanda el nodo **Opciones de edición** , elija el vínculo **sobrescribir XML generado y editar manifiesto en el editor XML** y, a continuación, elija el botón **sí** .

     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.

## <a name="enable-the-package-designer"></a>Habilitar el diseñador de paquetes
 Puede volver a habilitar el diseñador de paquetes para personalizar el archivo de *manifest.xml* .

#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador

1. En el **Diseñador de paquetes**, elija el vínculo **descartar cambios de manifiesto y volver a habilitar el diseñador** y, a continuación, elija el botón **sí** .

     La plantilla se actualiza con el texto original y se pierden los cambios en el XML.

## <a name="see-also"></a>Vea también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
