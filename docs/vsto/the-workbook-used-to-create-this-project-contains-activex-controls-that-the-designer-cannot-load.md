---
title: El libro contiene controles ActiveX que no se pueden cargar
description: Obtenga información acerca de cómo puede resolver el error que se produce cuando un libro contiene controles ActiveX que no se pueden cargar.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 7257e3940af72f344906642adc51a1dd98cb3f25
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524179"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>El libro contiene controles ActiveX que no se pueden cargar

  El error "el libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar" aparece cuando se agrega un control a un documento de Word o una hoja de cálculo de Excel mediante programación, se guarda el documento o el libro y, a continuación, se crea una nueva solución de nivel de documento basada en el documento o libro.

 La información que describe el tipo administrado del control no se guarda con el documento ni con el libro. Al crear una nueva solución basada en ese documento o libro, Visual Studio no tiene bastante información para cargar el control en el diseñador del elemento host.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Abra el documento o el libro.

2. Quite los controles que se agregaron en tiempo de ejecución. Para ello, selecciónelos en el documento o en el libro y presione la tecla **Supr** .

3. Cree una solución en el nivel del documento basada en el documento o en el libro.

## <a name="see-also"></a>Consulte también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
