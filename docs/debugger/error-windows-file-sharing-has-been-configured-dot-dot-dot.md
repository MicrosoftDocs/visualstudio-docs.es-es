---
title: 'Error: Se ha configurado el uso compartido de archivos de Windows... | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af92ff07958656d350f30fb6b7f8f2a2ea5898f1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460057"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Error: Se ha configurado el uso compartido de archivos de Windows…
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