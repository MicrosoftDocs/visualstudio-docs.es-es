---
title: Referencia de la API no administrada (desarrollo de Office en Visual Studio)
description: La referencia de la API no administrada se usa para ayudar a los complementos de VSTO administrados por carga. También puede crear su propio componente de cargador de complementos de VSTO implementando esta interfaz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908548"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de la API no administrada (desarrollo de Office en Visual Studio)

A partir del sistema Microsoft Office de 2007, las aplicaciones de Office usan la interfaz de [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) para llamar a un componente del cargador de complementos de VSTO que se incluye con [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Este componente se usa para ayudar a los complementos de VSTO administrados por carga. Puede crear su propio componente de cargador de complementos de VSTO implementando esta interfaz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>En esta sección

[Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)

Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.
