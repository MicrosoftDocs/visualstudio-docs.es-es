---
title: 'Cómo: agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
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
ms.openlocfilehash: 7875401dee07961d63de6c7b71a97e647c21a0b7
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755617"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Cómo: agregar y quitar características y elementos de un paquete mediante el Explorador de empaquetado
  Para configurar un paquete para implementar características y elementos de SharePoint, puede usar el Explorador de empaquetado. Puede ajustar los elementos de proyecto de SharePoint y características en el archivo WSP.  
  
 Como alternativa, puede usar el Diseñador de paquetes para ver y cambiar el orden de las características que se va a cambiar el orden de activación. Para obtener más información, consulte [Cómo: agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="open-the-packaging-explorer"></a>Abra el Explorador de empaquetado  
 Puede usar el procedimiento siguiente para abrir el Explorador de empaquetado, si su solución de Visual Studio tiene al menos un proyecto de SharePoint. Como alternativa, el Explorador de empaquetado se abre automáticamente cuando se ve un diseñador de característica o paquete. Después de cerrar todos los diseñadores de paquetes y características, también se cierra el Explorador de empaquetado.  
  
#### <a name="to-open-the-packaging-explorer"></a>Para abrir el Explorador de empaquetado  
  
1.  En la barra de menús, elija **vista** > **Other Windows** > **Explorador de empaquetado**.  
  
     El **Explorador de empaquetado** aparece en el **cuadro de herramientas**.  
  
## <a name="adding-a-feature-to-a-package"></a>Agregar una característica a un paquete  
 Puede agregar características nuevas y existentes a un paquete mediante el Explorador de empaquetado.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Para agregar una característica de SharePoint
  
1.  Abra el **Explorador de empaquetado**, abra el menú contextual para el proyecto y, a continuación, elija **Agregar característica**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Para mover una característica de SharePoint existente  
  
1.  Abra el **Explorador de empaquetado**y, a continuación, realice uno de los pasos siguientes:  
  
    -   Arrastre un **característica** desde un proyecto a otro proyecto.  
  
    -   Abra el menú contextual de una característica, elija **cortar**, abra el menú contextual para el proyecto al que desea mover la característica y, a continuación, elija **pegar**.  
  
    > [!NOTE]  
    >  Utilice este procedimiento si tiene más de un proyecto de SharePoint en la solución.  
  
## <a name="validate-a-feature-or-package"></a>Validar una característica o paquete  
 Puede identificar posibles problemas en los paquetes y las características de SharePoint mediante la validación de los archivos. Errores y advertencias se muestran en la ventana de salida y la ventana Lista de errores.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Para validar un paquete o una característica de SharePoint
  
1.  Abra el **Explorador de empaquetado**.  
  
2.  Abra un menú contextual para una característica o paquete y, a continuación, elija **validar**.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
