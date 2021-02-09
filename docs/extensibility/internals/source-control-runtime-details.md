---
title: Detalles de tiempo de ejecución del control de código fuente | Microsoft Docs
description: Obtenga información sobre cómo se agrega un proyecto al control de código fuente, bien cuando un usuario agrega un archivo al proyecto en el control de código fuente o a través de un controlador de automatización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 213b0096f2bea541fa55840f8f1ea78e8f195cd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905750"
---
# <a name="source-control-runtime-details"></a>Detalles de tiempo de ejecución del control de código fuente
Un proyecto se agrega al control de código fuente cuando el usuario agrega un archivo al control de código fuente, o a través de un controlador de automatización, como un asistente. Un proyecto no especifica para sí mismo que está bajo control de código fuente; admite el control de código fuente, pero debe agregarse manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrar con un paquete de control de código fuente
 Cuando se agrega un archivo del proyecto al control de código fuente, el entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> a para proporcionar cuatro cadenas opacas que el sistema de control de código fuente utiliza como cookies. Almacene estas cadenas en el archivo del proyecto. Estas cadenas se deben pasar al código auxiliar de control de código fuente (el componente de Visual Studio que administra los paquetes de control de código fuente) al iniciar el tipo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Esto, a su vez, carga el paquete de control de código fuente adecuado y reenvía la llamada a su implementación de `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
