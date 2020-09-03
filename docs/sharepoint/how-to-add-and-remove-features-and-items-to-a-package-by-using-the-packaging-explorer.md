---
title: 'Explorador de empaquetado: agregar & quitar características & elementos para empaquetar'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3ea7e30737855cbbb9434e8763f4903d80b82da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014561"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Cómo: agregar y quitar características y elementos de un paquete mediante el explorador de empaquetado
  Para configurar un paquete para implementar elementos y características de SharePoint, puede usar el explorador de empaquetado. Puede ajustar los elementos y las características del proyecto de SharePoint dentro del archivo. wsp.

 Como alternativa, puede utilizar el diseñador de empaquetado para ver y volver a ordenar las características para cambiar el orden de activación. Para obtener más información, vea [Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Abrir el explorador de empaquetado
 Puede usar el procedimiento siguiente para abrir el explorador de empaquetado, si la solución de Visual Studio tiene al menos un proyecto de SharePoint. Como alternativa, el explorador de empaquetado se abre automáticamente al ver un diseñador de características o paquetes. Después de cerrar todos los diseñadores de características y paquetes, el explorador de empaquetado también se cierra.

#### <a name="to-open-the-packaging-explorer"></a>Para abrir el explorador de empaquetado

1. En la barra de menús, elija **Ver**  >  **otro**  >  **Explorador de empaquetado**de Windows.

     El **Explorador de empaquetado** aparece en el **cuadro de herramientas**.

## <a name="adding-a-feature-to-a-package"></a>Agregar una característica a un paquete
 Puede agregar características nuevas y existentes a un paquete mediante el explorador de empaquetado.

#### <a name="to-add-a-sharepoint-feature"></a>Para agregar una característica de SharePoint

1. Abra el **Explorador de empaquetado**, abra el menú contextual del proyecto y, a continuación, elija **Agregar característica**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Para trasladar una característica existente de SharePoint

1. Abra el **Explorador de empaquetado**y, a continuación, realice uno de los pasos siguientes:

    - Arrastre una **característica** de un proyecto a otro proyecto.

    - Abra el menú contextual de una característica, elija **cortar**, abra el menú contextual del proyecto al que desea desplace la característica y, a continuación, elija **pegar**.

    > [!NOTE]
    > Utilice este procedimiento si tiene más de un proyecto de SharePoint en la solución.

## <a name="validate-a-feature-or-package"></a>Validar una característica o un paquete
 Puede identificar los posibles problemas en las características y los paquetes de SharePoint mediante la validación de los archivos. Las advertencias y los errores se muestran en la ventana de salida y Lista de errores ventana.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Para validar una característica o un paquete de SharePoint

1. Abra el **Explorador de empaquetado**.

2. Abra un menú contextual de una característica o un paquete y, a continuación, elija **validar**.

## <a name="see-also"></a>Consulte también
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
