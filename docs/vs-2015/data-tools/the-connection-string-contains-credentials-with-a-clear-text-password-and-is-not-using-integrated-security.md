---
title: La cadena de conexión contiene credenciales con una contraseña de texto no cifrado y no usa seguridad integrada | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d1be15ffdc204512c3034662b6ca24955869f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575306"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La cadena de conexión contiene credenciales con una contraseña en texto no cifrado y no usa seguridad integrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [la cadena de conexión contiene credenciales con una contraseña de texto no cifrado y no usa seguridad integrada](https://docs.microsoft.com/visualstudio/data-tools/the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security).  
  
  
¿Desea guardar la cadena de conexión en el archivo DBML y archivos de configuración de la aplicación actuales con esta información confidencial?  Haga clic en No para guardar la cadena de conexión sin la información confidencial.  
  
 Al trabajar con conexiones de datos que incluyen información confidencial (contraseñas incluidas en la cadena de conexión), se puede optar por guardar la cadena de conexión en el archivo DBML y el archivo de configuración de la aplicación de un proyecto, con o sin la información confidencial.  
  
> [!WARNING]
>  De forma explícita el **conexión** propiedades **configuración de la aplicación** propiedad **False** agregará la contraseña para el archivo DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Para guardar la cadena de conexión con la información confidencial en la configuración de la aplicación del proyecto  
  
-   Haga clic en **Sí**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación. La cadena de conexión incluye la información confidencial en texto sin formato. El archivo DBML no contiene ninguna información confidencial.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Para guardar la cadena de conexión sin la información confidencial en la configuración de la aplicación del proyecto  
  
-   Haga clic en **No**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación, pero no se incluye la contraseña.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

