---
title: 'Cómo: depurar clientes y servidores mediante la depuración RPC COM | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4222bdfcc2f54159e69bd89e30da3c0e85d7a5b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268104"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Cómo: Depurar clientes y servidores COM mediante la depuración RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar la depuración RPC (llamada a procedimiento remoto) para depurar aplicaciones COM cliente-servidor. Debe habilitar la depuración RPC para poder utilizarla. Con la depuración RPC habilitada, cuando entra en la llamada al servidor desde el cliente, el depurador se adjunta al servidor y le permite depurar el código. Una vez asociado el depurador, podrá utilizar todas sus características con los procesos del servidor y del cliente.  
  
### <a name="to-enable-rpc-debugging"></a>Para habilitar la depuración RPC  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, haga clic en el **depuración** carpeta.  
  
3.  Haga clic en el **nativo** página.  
  
4.  Seleccione el **depuración RPC** casilla de verificación.  
  
    > [!NOTE]
    >  Para depurar las llamadas RPC, debe tener privilegios de Administrador o Usuario avanzado.  
  
    > [!NOTE]
    >  La introducción paso a paso de las RPC en un servidor remoto donde se ejecuta Microsoft Windows Vista sólo funcionará si se asocia un depurador nativo al servidor remoto. De lo contrario, se producirá un error en la llamada RPC sin que se muestre ningún mensaje de error. Si no, se completará la llamada RPC, pero no funcionará la ejecución paso a paso en la llamada RPC.  
  
## <a name="see-also"></a>Vea también  
 [Servidor COM y un contenedor de depuración](../debugger/com-server-and-container-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)



