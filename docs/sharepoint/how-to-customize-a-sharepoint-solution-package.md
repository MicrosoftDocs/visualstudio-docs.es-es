---
title: "Cómo: personalizar un paquete de solución de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d07f03c1aed1c2e85e65bd10a89bd62138d571c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Cómo: Personalizar un paquete de solución de SharePoint
  Puede utilizar el Diseñador de paquetes para crear y personalizar un paquete (.wsp). Por ejemplo, puede agregar elementos de proyecto de SharePoint y características, especifique si el servidor Web se restablece cuando se implementa la solución y establecer el tipo de servidor de implementación.  
  
## <a name="opening-the-package-designer"></a>Abrir el Diseñador de paquetes  
  
#### <a name="to-open-the-package-designer"></a>Para abrir el Diseñador de paquetes  
  
-   En **el Explorador de soluciones**, haga doble clic en **paquete**, o elija **Diseñador de vistas** en el menú contextual de **paquete**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Ver el archivo de manifiesto empaquetado  
 Puede utilizar el Diseñador de paquetes para modificar y generar el archivo de manifiesto empaquetado. A continuación, puede ver el código XML de este archivo en Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Para ver el archivo de origen XML  
  
1.  En el **Diseñador de paquetes**, elija **manifiesto**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante el Explorador de soluciones  
  
1.  En **el Explorador de soluciones**, elija **mostrar todos los archivos**.  
  
2.  Expanda el paquete, expanda Package.package y, a continuación, abra el archivo Package.Template.xml.  
  
    > [!NOTE]  
    >  Al abrir el archivo XML de manifiesto de la plantilla de paquete, los archivos se validan automáticamente y puede pasar por alto las advertencias que aparecen en la ventana Lista de errores.  
  
## <a name="changing-the-manifest-template"></a>Cambiar la plantilla de manifiesto  
 Puede cambiar el código XML para el archivo de manifiesto empaquetado en el Editor XML de Visual Studio o en el panel de la plantilla de manifiesto. Los cambios en el código XML se combinan en el archivo de manifiesto empaquetado para el paquete.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto utilizando el Editor XML  
  
1.  En el **Diseñador de paquetes**, elija la **manifiesto** , expanda la **Editar opciones** nodo y, a continuación, elija la **abierto en el Editor de XML** vínculo.  
  
     Cambios en el código XML se combinan en el archivo de manifiesto empaquetado.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto utilizando el recuadro plantilla de manifiesto  
  
1.  En el **Diseñador de paquetes**, elija la **manifiesto** , expanda la **Editar opciones** nodo y, a continuación, cambie el código XML que aparece en el panel de la plantilla de manifiesto.  
  
     Los cambios en el XML aparecen en la **vista previa del manifiesto empaquetado** panel.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Sobrescribiendo el archivo de manifiesto empaquetado  
 Puede deshabilitar al diseñador de paquetes y crear el archivo manifest.xml manualmente. La primera vez que lleva a cabo este procedimiento, la configuración actual en el Diseñador de paquetes se guarda en el archivo XML de plantilla de paquete. A continuación, puede modificar o sobrescribir el código XML.  
  
> [!NOTE]  
>  Si agrega o quitar características y elementos de proyecto de SharePoint en el archivo XML mientras está deshabilitado el Diseñador de paquetes, estos elementos de proyecto y características no están empaquetados.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador  
  
1.  En el **Diseñador de paquetes**, elija la **manifiesto** ficha.  
  
2.  .  
  
3.  Expanda el **Editar opciones** nodo, elija la **sobrescribir generado XML y editar el manifiesto en el editor XML** vincular y, a continuación, elija la **Sí** botón.  
  
     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.  
  
## <a name="enabling-the-package-designer"></a>Habilitar al diseñador de paquetes  
 Puede volver a habilitar el Diseñador de paquetes para personalizar el archivo manifest.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador  
  
1.  En el **Diseñador de paquetes**, elija la **descarte manifiestos modificaciones y volver a habilitar el diseñador** vincular y, a continuación, elija la **Sí** botón.  
  
     La plantilla se actualiza con el texto original y se perderán los cambios realizados en el código XML.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  