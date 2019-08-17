---
title: Referencia de la API no administrada (desarrollo de Office en Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
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
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551326"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de la API no administrada (desarrollo de Office en Visual Studio)

A partir del sistema Microsoft Office de 2007, las aplicaciones de Office usan la interfaz de [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) para llamar a un componente del cargador de complementos de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]VSTO que se incluye con. Este componente se usa para ayudar a los complementos de VSTO administrados por carga. Puede crear su propio componente de cargador de complemento de VSTO implementando esta interfaz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>En esta sección

[Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)

Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.
