---
title: 'Cómo: personalizar un paquete de solución de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd1ebe9e49a0b3e26d090fdbbdbbe4dd37c0344a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119883"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Cómo: personalizar un paquete de solución de SharePoint
  Puede usar el Diseñador de paquetes para crear y personalizar un paquete (*.wsp*). Por ejemplo, puede agregar elementos de proyecto de SharePoint y características, especifique si el servidor Web se restablece cuando se implementa la solución y establecer el tipo de servidor de implementación.  
  
## <a name="open-the-package-designer"></a>Abra el Diseñador de paquetes  
  
#### <a name="to-open-the-package-designer"></a>Para abrir el Diseñador de paquetes
  
-   En **el Explorador de soluciones**, haga doble clic en **paquete**, o elija **Diseñador de vistas** en el menú contextual de **paquete**.  
  
## <a name="view-the-packaged-manifestffile"></a>Ver el manifestfFile empaquetada  
 Puede usar el Diseñador de paquetes para modificar y generar el archivo de manifiesto empaquetado. A continuación, puede ver el código XML de este archivo en Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Para ver el archivo de origen XML  
  
1.  En el **Diseñador de paquetes**, elija **manifiesto**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para ver el archivo de manifiesto empaquetado mediante el Explorador de soluciones  
  
1.  En **el Explorador de soluciones**, elija **mostrar todos los archivos**.  
  
2.  Expanda el paquete, expanda Package.package y, a continuación, abra el *Package.Template.xml* archivo.  
  
    > [!NOTE]  
    >  Al abrir el archivo de manifiesto XML para la plantilla de paquete, los archivos se validan automáticamente y puede omitir las advertencias que aparecen en la ventana Lista de errores.  
  
## <a name="change-the-manifest-template"></a>Cambiar la plantilla de manifiesto  
 Puede cambiar el código XML para el archivo de manifiesto empaquetado en el Editor XML de Visual Studio o en el panel de la plantilla de manifiesto. Los cambios en el código XML se combinan en el archivo de manifiesto empaquetado para el paquete.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para cambiar la plantilla de manifiesto mediante el Editor XML  
  
1.  En el **Diseñador de paquetes**, elija el **manifiesto** , expanda el **Editar opciones** nodo y, a continuación, elija el **abierto en el Editor XML** vínculo.  
  
     Los cambios realizados en el código XML se combinan en el archivo de manifiesto empaquetado.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para cambiar la plantilla de manifiesto mediante el panel de la plantilla de manifiesto  
  
1.  En el **Diseñador de paquetes**, elija el **manifiesto** , expanda el **Editar opciones** nodo y, a continuación, cambie el código XML que aparece en el panel de la plantilla de manifiesto.  
  
     Los cambios en el XML aparecen en la **vista previa del manifiesto empaquetado** panel.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Sobrescribir el archivo de manifiesto empaquetado  
 Puede deshabilitar el Diseñador de paquetes y crear el *manifest.xml* archivo manualmente. La primera vez que realice este procedimiento, la configuración actual en el Diseñador de paquetes se guarda en el archivo XML de plantilla de paquete. A continuación, puede modificar o sobrescribir el código XML.  
  
> [!NOTE]  
>  Si agrega o quita elementos de proyecto de SharePoint y las características en el archivo XML mientras está deshabilitado el Diseñador de paquetes, estos elementos de proyecto y características no están empaquetadas.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para sobrescribir el archivo de manifiesto empaquetado deshabilitando el diseñador  
  
1.  En el **Diseñador de paquetes**, elija el **manifiesto** ficha.  
  
2.  Expanda el **Editar opciones** nodo, elija el **sobrescritura generado XML y editar el manifiesto en el editor XML** vincular y, a continuación, elija el **Sí** botón.  
  
     La plantilla se actualiza con el archivo de manifiesto empaquetado actual.  
  
## <a name="enable-the-package-designer"></a>Habilitar al diseñador de paquetes  
 Puede volver a habilitar el Diseñador de paquetes para personalizar el *manifest.xml* archivo.  
  
#### <a name="to-re-enable-the-designer"></a>Para volver a habilitar el diseñador  
  
1.  En el **Diseñador de paquetes**, elija el **descarte manifiesto modificaciones y vuelva a habilitar el diseñador** vincular y, a continuación, elija el **Sí** botón.  
  
     La plantilla se actualiza con el texto original y se pierden los cambios realizados en el código XML.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
