---
title: El libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537350"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>El libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar
  Este error aparece cuando se agrega un control a un documento de Word o a una hoja de cálculo de Excel, se guarda el documento o libro mediante programación y, a continuación, se crea una nueva solución en el nivel del documento basada en el documento o libro.

 La información que describe el tipo administrado del control no se guarda con el documento ni con el libro. Al crear una nueva solución basada en ese documento o libro, Visual Studio no tiene bastante información para cargar el control en el diseñador del elemento host.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Abra el documento o el libro.

2. Quite los controles que se agregaron en tiempo de ejecución. Para ello, selecciónelos en el documento o en el libro y presione la tecla **Supr** .

3. Cree una solución en el nivel del documento basada en el documento o en el libro.

## <a name="see-also"></a>Consulte también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
