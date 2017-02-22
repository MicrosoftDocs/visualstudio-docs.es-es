---
title: "CodeIndex (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeIndex (comando) [Team Foundation Server]"
  - "herramientas de la línea de comandos [Team Foundation Server]"
  - "TFSConfig"
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CodeIndex (Comando)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use el comando **CodeIndex** para administrar la indización de código en Team Foundation Server.  Por ejemplo, puede que desee restablecer el índice para corregir la información de CodeLens o desactivar la indización para investigar los problemas de rendimiento del servidor.  
  
 **Permisos necesarios**  
  
 Para usar el comando **CodeIndex**, debe ser un miembro del grupo de seguridad **Team Foundation Administrators**.  Consultar [Permission reference for Team Foundation Server](../Topic/Permission%20reference%20for%20Team%20Foundation%20Server.md)  
  
> [!NOTE]
>  Aunque haya iniciado sesión con credenciales administrativas, debe abrir una ventana de símbolo del sistema con privilegios elevados para ejecutar este comando.  También debe ejecutar este comando desde la capa de aplicación de Team Foundation.  
  
## Sintaxis  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### Parámetros  
  
|**Argumento**|**Descripción**|  
|-------------------|---------------------|  
|`CollectionName`|Especifica el nombre de la colección de proyectos de equipo.  Si el nombre contiene espacios, inclúyalo entre comillas, por ejemplo, “Sitio web de Fabrikam”.|  
|`CollectionId`|Especifica el número de identificación de la colección de proyectos de equipo.|  
|`ServerPath`|Especifica la ruta de acceso a un archivo de código.|  
  
|**Opción**|**Descripción**|  
|----------------|---------------------|  
|**\/indexingStatus**|Muestra el estado y la configuración del servicio de indización de código.|  
|**\/setIndexing:**\[ on &#124; off &#124; keepupOnly \]|-   **on**: inicia la indización de todos los conjuntos de cambios.<br />-   **off**: detiene la indización de todos los conjuntos de cambios.<br />-   **keepupOnly**: detiene la indización de los conjuntos de cambios creados previamente e inicia solamente la indización de nuevos conjuntos de cambios.|  
|**\/ignoreList:**\[ add &#124; remove &#124; removeAll &#124; view \] `ServerPath`<br /><br /> Puede usar el carácter comodín \(\*\) al principio, al final o en ambos extremos de la ruta de acceso del servidor.|Especifica una lista de archivos de código, con sus rutas de acceso, que no desea que estén indizados.<br /><br /> -   **add**: agrega el archivo que no desea indizar a la lista de archivos ignorados.<br />-   **remove**: quita el archivo que desea indizar de la lista de archivos ignorados.<br />-   **removeAll**: borra la lista de archivos omitidos e inicia la indización de todos los archivos.<br />-   **view**: permite ver todos los archivos que no se están indizando.|  
|**\/listLargeFiles \[\/fileCount:** `FileCount` **\/minSize:** `MinSize`\]|Muestra el número especificado de archivos que supera el tamaño especificado en KB.  Posteriormente puede usar la opción **\/ignoreList** para excluir estos archivos de la indización.|  
|**\/reindexAll**|Borra datos anteriormente indizados y reinicia la indización.|  
|**\/destroyCodeIndex \[\/noPrompt\]**|Elimina el índice de código y quita todos los datos indizados.  No requiere confirmación si usa la opción **\/noPrompt**.|  
|**\/temporaryDataSizeLimit**:\[ view &#124; \<`SizeInGBs`\> &#124; disable \]|Controla la cantidad de datos temporales creados por CodeLens al procesar los conjuntos de cambios.  El límite predeterminado es de 2 GB.<br /><br /> -   **view**: muestra el límite de tamaño actual.<br />-   `SizeInGBs`: cambia el límite de tamaño.<br />-   **disable**: quita el límite de tamaño.<br /><br /> Este límite se comprueba antes de que CodeLens procese un conjunto de cambios nuevo.  Si los datos temporales superan este límite, CodeLens se pausará al procesar los conjuntos de cambios antiguos, pero no los nuevos.  CodeLens comenzará a procesar de nuevo cuando los datos se hayan limpiado y no superen este límite.  La limpieza se ejecuta automáticamente una vez al día.  Esto significa que los datos temporales podrían superar este límite hasta que empiece a ejecutarse la limpieza.|  
|**\/indexHistoryPeriod**:\[ view &#124; all &#124; \<`NumberOfMonths`\> \]|Controla durante cuánto tiempo se indizará el historial de cambios.  Esto afecta a la cantidad de historial mostrado por CodeLens.  El límite predeterminado son 12 meses.  Esto significa que CodeLens solo muestra el historial de cambios de los últimos 12 meses.<br /><br /> -   **view**: muestra el número actual de meses.<br />-   **all**: indiza todo el historial de cambios.<br />-   `NumberOfMonths`: cambia el número de meses usados para indizar el historial de cambios.|  
|**\/collectionName:** `CollectionName`|Especifica el nombre de la colección de proyectos de equipo en la que se va a ejecutar el comando **CodeIndex**.  Se requiere si no se usa **\/CollectionId**.|  
|**\/collectionId:** `CollectionId`|Especifica el número de identificación de la colección de proyectos de equipo en la que se va a ejecutar el comando **CodeIndex**.  Se requiere si no se usa **\/CollectionName**.|  
  
## Ejemplos  
  
> [!NOTE]
>  Las empresas, las organizaciones, los productos, los nombres de dominio, las direcciones de correo electrónico, los logotipos, los usuarios, las ubicaciones y los eventos que se citan a modo de ejemplo son ficticios.  No se pretende indicar, ni debe deducirse, ninguna asociación con compañías, organizaciones, productos, dominios, direcciones de correo electrónico, logotipos, personas, lugares o hechos reales.  
  
 Para ver el estado y la configuración de la indización de código:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Para iniciar la indización de todos los conjuntos de cambios:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Para detener la indización de los conjuntos de cambios creados previamente e iniciar solo la indización de nuevos conjuntos de cambios:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Para buscar hasta 50 archivos de más de 10 KB:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Para excluir un archivo concreto de la indización y agregarlo a la lista de archivos omitidos:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Para ver todos los archivos que no están indizados:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Para borrar datos indizados previamente y reiniciar la indización:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Para guardar todo el historial del conjunto de cambios:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Para quitar el límite de tamaño de los datos temporales de CodeLens y seguir indexando independientemente del tamaño de los datos temporales:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Para eliminar el índice de código con confirmación:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## Vea también  
 [Managing server configuration with TFSConfig](http://msdn.microsoft.com/es-es/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Command\-line tools for TFS](http://msdn.microsoft.com/es-es/be8c997a-b97b-4e59-97f5-04db0a601a6c)