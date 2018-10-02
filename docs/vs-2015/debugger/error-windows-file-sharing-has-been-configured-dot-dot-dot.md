---
title: 'Error: el uso compartido de archivos de Windows se configuró... | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc4d3fb02b1c7c9d5003f82fbe42be73c93d6eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575243"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Error: Se ha configurado el uso compartido de archivos de Windows…
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: se ha configurado el uso compartido de archivos de Windows... ](https://docs.microsoft.com/visualstudio/debugger/error-windows-file-sharing-has-been-configured-dot-dot-dot).  
  
Se ha configurado el uso compartido de archivos de Windows para que se conecte al equipo remoto mediante un nombre de usuario distinto. Este proceso no es compatible con la depuración remota   
  
 Se ha configurado el uso compartido de archivos de Windows para que se conecte al equipo remoto mediante un nombre de usuario distinto. Este proceso no es compatible con la depuración remota.  
  
 Para corregir este error, inicie sesión en el equipo con el otro nombre de cuenta o cambie el uso compartido de archivos para que utilice el nombre de cuenta con el que lleva a cabo la depuración.  
  
 Si desea conectarse al equipo remoto con este nombre de usuario, primero debe desconectarse del equipo remoto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Inicie sesión en el equipo local, aquel desde el cual lleva acabo la depuración, con el otro nombre de cuenta.  
  
     -O bien-  
  
     . Desconecte del equipo remoto y, a continuación, vuelva a configurar el uso compartido de archivos para conectarse al otro equipo mediante su nombre de cuenta:  
  
    1.  En el **iniciar** menú, elija **Accesorios**y, a continuación, haga clic en **símbolo**.  
  
    2.  En la línea de comandos de Windows, escriba:  
  
         `net use /delete computer_name`  
  
    3.  Cambie la configuración del uso compartido de archivos mediante cualquiera de los métodos documentados en la ayuda de Windows.



