---
title: Referencia de la API no administrada (desarrollo de Office en Visual Studio)
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79f48e7771b3e62c0c58fbc59bd9f9b534069d71
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584430"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de la API no administrada (desarrollo de Office en Visual Studio)

A partir del sistema Microsoft Office de 2007, las aplicaciones de Office usan la interfaz de [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) para llamar a un componente del cargador de complementos de VSTO que se incluye con [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Este componente se usa para ayudar a los complementos de VSTO administrados por carga. Puede crear su propio componente de cargador de complementos de VSTO implementando esta interfaz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>En esta sección

[Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)

Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.
