---
title: CodeIndex (Comando)| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 350708309cdc7a65b8c991454704dc9212f20ef8
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="codeindex-command"></a>CodeIndex (Comando)
Use el comando **CodeIndex** para administrar la indexación de código en Team Foundation Server. Por ejemplo, puede que desee restablecer el índice para corregir la información de CodeLens o desactivar la indización para investigar los problemas de rendimiento del servidor.  
  
 **Permisos necesarios**  
  
 Para usar el comando **CodeIndex**, debe ser miembro del grupo de seguridad **Administradores de Team Foundation**. Vea [Permisos y grupos definidos en Team Services y TFS](https://www.visualstudio.com/docs/setup-admin/permissions).  
  
> [!NOTE]
>  Aunque haya iniciado sesión con credenciales administrativas, debe abrir una ventana de símbolo del sistema con privilegios elevados para ejecutar este comando. También debe ejecutar este comando desde la capa de aplicación de Team Foundation.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|**Argumento**|**Descripción**|  
|------------------|---------------------|  
|`CollectionName`|Especifica el nombre de la colección de proyectos de equipo. Si el nombre contiene espacios, inclúyalo entre comillas, por ejemplo, “Sitio web de Fabrikam”.|  
|`CollectionId`|Especifica el número de identificación de la colección de proyectos de equipo.|  
|`ServerPath`|Especifica la ruta de acceso a un archivo de código.|  
  
|**Opción**|**Descripción**|  
|----------------|---------------------|  
|**/indexingStatus**|Muestra el estado y la configuración del servicio de indización de código.|  
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: inicia la indexación de todos los conjuntos de cambios.<br />-   **off**: detiene la indexación de todos los conjuntos de cambios.<br />-   **keepupOnly**: detiene la indexación de los conjuntos de cambios creados previamente e inicia solo la indexación de los nuevos conjuntos de cambios.|  
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Puede usar el carácter comodín (*) al principio, al final o en ambos extremos de la ruta de acceso del servidor.|Especifica una lista de archivos de código, con sus rutas de acceso, que no desea que estén indizados.<br /><br /> -   **add**: agrega el archivo que no quiere indexar a la lista de archivos omitidos.<br />-   **remove**: quita el archivo que quiere indexar de la lista de archivos omitidos.<br />-   **removeAll**: borra la lista de archivos omitidos e inicia la indexación de todos los archivos.<br />-   **view**: permite ver todos los archivos que no se están indexando.|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Muestra el número especificado de archivos que supera el tamaño especificado en KB. Posteriormente, puede usar la opción **/ignoreList** para excluir estos archivos de la indexación.|  
|**/reindexAll**|Borra datos anteriormente indizados y reinicia la indización.|  
|**/destroyCodeIndex [/noPrompt]**|Elimina el índice de código y quita todos los datos indizados. No requiere confirmación si usa la opción **/noPrompt**.|  
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Controla la cantidad de datos temporales creados por CodeLens al procesar los conjuntos de cambios. El límite predeterminado es de 2 GB.<br /><br /> -   **view**: muestra el límite de tamaño actual.<br />-   `SizeInGBs`: cambia el límite de tamaño.<br />-   **disable**: quita el límite de tamaño.<br /><br /> Este límite se comprueba antes de que CodeLens procese un conjunto de cambios nuevo. Si los datos temporales superan este límite, CodeLens se pausará al procesar los conjuntos de cambios antiguos, pero no los nuevos. CodeLens comenzará a procesar de nuevo cuando los datos se hayan limpiado y no superen este límite. La limpieza se ejecuta automáticamente una vez al día. Esto significa que los datos temporales podrían superar este límite hasta que empiece a ejecutarse la limpieza.|  
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Controla durante cuánto tiempo se indizará el historial de cambios. Esto afecta a la cantidad de historial mostrado por CodeLens. El límite predeterminado son 12 meses. Esto significa que CodeLens solo muestra el historial de cambios de los últimos 12 meses.<br /><br /> -   **view**: muestra el número actual de meses.<br />-   **all**: indexa todo el historial de cambios.<br />-   `NumberOfMonths`: cambia el número de meses usados para indexar el historial de cambios.|  
|**/collectionName:** `CollectionName`|Especifica el nombre de la colección de proyectos de equipo en la que se va a ejecutar el comando **CodeIndex**. Es obligatorio si no usa **/CollectionId**.|  
|**/collectionId:** `CollectionId`|Especifica el número de identificación de la colección de proyectos de equipo en la que se va a ejecutar el comando **CodeIndex**. Es obligatorio si no usa **/CollectionName**.|  
  
## <a name="examples"></a>Ejemplos  
  
> [!NOTE]
>  Las empresas, las organizaciones, los productos, los nombres de dominio, las direcciones de correo electrónico, los logotipos, los usuarios, las ubicaciones y los eventos que se citan a modo de ejemplo son ficticios.  No se pretende indicar, ni debe deducirse, ninguna asociación con compañías, organizaciones, productos, dominios, direcciones de correo electrónico, logotipos, personas, lugares o hechos reales.  
  
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
  
## <a name="see-also"></a>Vea también

[Buscar cambios en el código y otro historial con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)  
[Managing server configuration with TFSConfig](/vsts/tfs-server/command-line/tfsconfig-cmd) (Administración de la configuración del servidor con TFSConfig)