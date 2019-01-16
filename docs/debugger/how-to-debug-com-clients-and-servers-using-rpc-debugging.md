---
title: Depurar clientes y servidores mediante la depuración RPC COM | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42ac7749052fdec3ef9f6cb318af4dc0302e1465
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269271"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Procedimiento Depurar clientes y servidores COM mediante la depuración RPC
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
 [Depurar en Visual Studio](../debugger/index.md)  
 [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)