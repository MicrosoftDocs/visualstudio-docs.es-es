---
title: "Cómo: agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bafa2a4310a77f9f5a9f061e378ac05f2896d4ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Cómo: Agregar y quitar características y elementos de un paquete con el explorador de empaquetado
  Para configurar un paquete para implementar elementos de SharePoint y las características, puede utilizar el Explorador de empaquetado. Puede ajustar los elementos de proyecto de SharePoint y características en el archivo .wsp.  
  
 Como alternativa, puede utilizar el Diseñador de paquetes para ver y cambiar el orden de las características que se va a cambiar el orden de activación. Para obtener más información, consulte [Cómo: agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Abra el Explorador de empaquetado  
 Puede usar el procedimiento siguiente para abrir el Explorador de empaquetado, si su solución de Visual Studio tiene al menos un proyecto de SharePoint. Como alternativa, el Explorador de empaquetado se abre automáticamente al ver un característica o diseñador de paquetes. Después de cerrar todos los diseñadores de paquetes y características, también se cierra el Explorador de empaquetado.  
  
#### <a name="to-open-the-packaging-explorer"></a>Para abrir el Explorador de empaquetado  
  
1.  En la barra de menús, elija **vista**, **otras ventanas**, **Explorador de empaquetado**.  
  
     El **Explorador de empaquetado** aparece en la **cuadro de herramientas**.  
  
## <a name="adding-a-feature-to-a-package"></a>Agregar una característica a un paquete  
 Puede agregar características nuevas y existentes a un paquete mediante el Explorador de empaquetado.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Para agregar una característica de SharePoint  
  
1.  Abra la **Explorador de empaquetado**, abra el menú contextual para el proyecto y, a continuación, elija **Agregar característica**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Para mover una característica de SharePoint existente  
  
1.  Abra la **Explorador de empaquetado**y, a continuación, realice uno de los siguientes pasos:  
  
    -   Arrastre un **característica** de un proyecto a otro proyecto.  
  
    -   Abra el menú contextual de una característica, elija **cortar**, abra el menú contextual para el proyecto al que desea mover la característica y, a continuación, elija **pegar**.  
  
    > [!NOTE]  
    >  Utilice este procedimiento si tiene más de un proyecto de SharePoint en la solución.  
  
## <a name="validating-a-feature-or-package"></a>Validar una característica o paquete  
 Puede identificar los posibles problemas en los paquetes y características de SharePoint mediante la validación de los archivos. Errores y advertencias se muestran en la ventana de salida y la ventana Lista de errores.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Para validar un paquete o una característica de SharePoint  
  
1.  Abra la **Explorador de empaquetado**.  
  
2.  Abrir un menú contextual para una característica o paquete y, a continuación, elija **validar**.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  