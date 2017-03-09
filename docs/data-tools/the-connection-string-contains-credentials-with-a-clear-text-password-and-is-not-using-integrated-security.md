---
title: "La cadena de conexi&#243;n contiene credenciales con una contrase&#241;a en texto no cifrado y no utiliza seguridad integrada. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La cadena de conexi&#243;n contiene credenciales con una contrase&#241;a en texto no cifrado y no utiliza seguridad integrada.
¿Desea guardar la cadena de conexión en el archivo DBML y los archivos de configuración de la aplicación actuales con esta información confidencial?Haga clic en No para guardar la cadena de conexión sin la información confidencial.  
  
 Al trabajar con conexiones de datos que incluyen información confidencial \(contraseñas incluidas en la cadena de conexión\), se puede optar por guardar la cadena de conexión en el archivo DBML y el archivo de configuración de la aplicación de un proyecto, con o sin la información confidencial.  
  
> [!WARNING]
>  Al establecer explícitamente la propiedad **Configuración de la aplicación** de las propiedades de la **Conexión** en **Falso**, se agregará la contraseña al archivo DBML.  
  
### Para guardar la cadena de conexión con la información confidencial en la configuración de la aplicación del proyecto  
  
-   Haga clic en **Sí**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación.La cadena de conexión incluye la información confidencial en texto sin formato.El archivo DBML no contiene ninguna información confidencial.  
  
### Para guardar la cadena de conexión sin la información confidencial en la configuración de la aplicación del proyecto  
  
-   Haga clic en **No**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación, pero no se incluye la contraseña.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)