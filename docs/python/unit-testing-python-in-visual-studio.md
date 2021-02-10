---
title: Código de pruebas unitarias de Python
description: La configuración de pruebas unitarias para código de Python en Visual Studio aprovecha al máximo las características del Explorador de pruebas con el fin de detectar, ejecutar y depurar las pruebas.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: aec13b3b35c75ecaad938cd3200f3af2a87d2441
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920689"
---
# <a name="set-up-unit-testing-for-python-code"></a>Configuración de pruebas unitarias para código de Python

Las pruebas unitarias son fragmentos de código que prueban otras unidades de código de una aplicación, normalmente funciones aisladas, clases, etc. Cuando una aplicación supera todas sus pruebas unitarias, al menos puede confiar en que su función de bajo nivel es correcta.

Python utiliza pruebas unitarias ampliamente para validar escenarios durante el diseño de un programa. La compatibilidad de Python en Visual Studio incluye características para descubrir, ejecutar y depurar pruebas unitarias dentro del contexto de su proceso de desarrollo, sin tener que ejecutar pruebas independientemente.

En este artículo se proporciona una descripción breve de las funcionalidades de las pruebas unitarias en Visual Studio con Python. Para más información sobre las pruebas unitarias en general, vea [Hacer una prueba unitaria del código](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end