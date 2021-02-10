---
title: Visualización de documentos de script | Microsoft Docs
description: Obtenga información sobre cómo ver documentos de script en el servidor de JavaScript en Visual Studio mediante el Explorador de soluciones.
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfaa4e2558d8d1f102b0e442e9c509313f860e4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853103"
---
# <a name="how-to-view-script-documents-javascript"></a>Procedimiento Visualización de documentos de script (JavaScript)

Los archivos de script de servidor son visibles en el Explorador de soluciones. Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción. Los archivos de script de cliente aparecen en el nodo **Documentos de script**.

Para algunos tipos de aplicaciones que generan páginas dinámicamente, es más fácil entrar en modo de interrupción y depurar cuando se establece un punto de interrupción a partir de un documento de script cargado en el explorador. De forma similar, puede agregar la instrucción `debugger` a partir de un documento de script cargado para entrar en modo de interrupción. En este artículo se muestra cómo visualizar estos documentos.

> [!NOTE]
> Antes de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts.

### <a name="to-view-a-server-side-script-document"></a>Para ver un documento de script de servidor

1. En el **Explorador de soluciones**, abra el nodo **\<Website Pathname>** .

2. Haga doble clic en el archivo de script que desee ver.

     El archivo de script de servidor se abre en una ventana de código fuente.

### <a name="to-view-a-client-side-script-document"></a>Para ver un documento de script de cliente

1. En el **Explorador de soluciones**, abra el nodo **Documentos de script**.

2. Haga doble clic en el archivo de script que desee ver.

     El archivo de script de cliente se abre en una ventana de código fuente.

## <a name="see-also"></a>Vea también
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)