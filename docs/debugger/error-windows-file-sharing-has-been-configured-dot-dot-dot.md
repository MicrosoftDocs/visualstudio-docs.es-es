---
title: 'Error: Uso compartido de archivos de Windows se ha configurado... | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 89224dc5394f248ea82d428731ef387cb705ff27
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850049"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Error: Se ha configurado el uso compartido de archivos de Windows…
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se ha configurado el uso compartido de archivos de Windows para que se conecte al equipo remoto mediante un nombre de usuario distinto. Este proceso no es compatible con la depuración remota   
  
 Se ha configurado el uso compartido de archivos de Windows para que se conecte al equipo remoto mediante un nombre de usuario distinto. Este proceso no es compatible con la depuración remota.  
  
 Para corregir este error, inicie sesión en el equipo con el otro nombre de cuenta o cambie el uso compartido de archivos para que utilice el nombre de cuenta con el que lleva a cabo la depuración.  
  
 Si desea conectarse al equipo remoto con este nombre de usuario, primero debe desconectarse del equipo remoto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1. Inicie sesión en el equipo local, aquel desde el cual lleva acabo la depuración, con el otro nombre de cuenta.  
  
     -O bien-  
  
     . Desconecte del equipo remoto y, a continuación, vuelva a configurar el uso compartido de archivos para conectarse al otro equipo mediante su nombre de cuenta:  
  
    1. En el menú **Inicio**, elija **Accesorios** y, a continuación, haga clic en **Símbolo del sistema**.  
  
    2. En la línea de comandos de Windows, escriba:  
  
         `net use /delete computer_name`  
  
    3. Cambie la configuración del uso compartido de archivos mediante cualquiera de los métodos documentados en la ayuda de Windows.
