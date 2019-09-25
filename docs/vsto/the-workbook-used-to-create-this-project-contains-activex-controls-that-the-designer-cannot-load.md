---
title: El libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 27feb1c6a85740d8a9287ce3a2a47800595e178a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253783"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>El libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar
  Este error aparece cuando se agrega un control a un documento de Word o a una hoja de cálculo de Excel, se guarda el documento o libro mediante programación y, a continuación, se crea una nueva solución en el nivel del documento basada en el documento o libro.

 La información que describe el tipo administrado del control no se guarda con el documento ni con el libro. Al crear una nueva solución basada en ese documento o libro, Visual Studio no tiene bastante información para cargar el control en el diseñador del elemento host.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Abra el documento o el libro.

2. Quite los controles que se agregaron en tiempo de ejecución. Para ello, selecciónelos en el documento o en el libro y presione la tecla **Supr** .

3. Cree una solución en el nivel del documento basada en el documento o en el libro.

## <a name="see-also"></a>Vea también
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
