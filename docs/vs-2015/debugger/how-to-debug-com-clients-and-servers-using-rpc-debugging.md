---
title: Filtrar Depurar clientes y servidores mediante la depuración RPC COM | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1235abfc6e8a2c384b02fd1d48a859063c058d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988861"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Filtrar Depurar clientes y servidores COM mediante la depuración RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar la depuración RPC (llamada a procedimiento remoto) para depurar aplicaciones COM cliente-servidor. Debe habilitar la depuración RPC para poder utilizarla. Con la depuración RPC habilitada, cuando entra en la llamada al servidor desde el cliente, el depurador se adjunta al servidor y le permite depurar el código. Una vez asociado el depurador, podrá utilizar todas sus características con los procesos del servidor y del cliente.  
  
### <a name="to-enable-rpc-debugging"></a>Para habilitar la depuración RPC  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, haga clic en la carpeta **Depuración**.  
  
3.  Haga clic en la página **Nativo**.  
  
4.  Active la casilla **Depuración RPC**.  
  
    > [!NOTE]
    >  Para depurar las llamadas RPC, debe tener privilegios de Administrador o Usuario avanzado.  
  
    > [!NOTE]
    >  La introducción paso a paso de las RPC en un servidor remoto donde se ejecuta Microsoft Windows Vista sólo funcionará si se asocia un depurador nativo al servidor remoto. De lo contrario, se producirá un error en la llamada RPC sin que se muestre ningún mensaje de error. Si no, se completará la llamada RPC, pero no funcionará la ejecución paso a paso en la llamada RPC.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de servidores y contenedores COM](../debugger/com-server-and-container-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
