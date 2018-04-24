---
title: 'Error: el uso compartido de archivos de Windows se configuró... | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 591b051cb6164f4c8d260be3de29833154c96255
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Error: Se ha configurado el uso compartido de archivos de Windows…
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