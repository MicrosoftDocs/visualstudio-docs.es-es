---
title: CodeIndex (Comando)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d472ec7d35b886dbc2294d2c3172b61d3b1e7702
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929224"
---
# <a name="codeindex-command"></a>CodeIndex (Comando)

Use el comando **CodeIndex** para administrar la indexación de código en Team Foundation Server. Por ejemplo, puede que desee restablecer el índice para corregir la información de CodeLens o desactivar la indización para investigar los problemas de rendimiento del servidor.

## <a name="required-permissions"></a>Permisos necesarios

Para usar el comando **CodeIndex**, debe ser miembro del grupo de seguridad **Administradores de Team Foundation**. Vea [Permissions and groups defined for Azure DevOps Services and TFS](/azure/devops/organizations/security/permissions?view=vsts) (Permisos y grupos definidos en Azure DevOps Services y TFS).

> [!NOTE]
> Aunque haya iniciado sesión con credenciales administrativas, debe abrir una ventana de símbolo del sistema con privilegios elevados para ejecutar este comando. También debe ejecutar este comando desde la capa de aplicación de Team Foundation.

## <a name="syntax"></a>Sintaxis

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parámetros

|**Argumento**|**Descripción**|
|------------------| - |
|`CollectionName`|Especifica el nombre de la colección de proyectos. Si el nombre contiene espacios, inclúyalo entre comillas, por ejemplo, “Sitio web de Fabrikam”.|
|`CollectionId`|Especifica el número de identificación de la colección de proyectos.|
|`ServerPath`|Especifica la ruta de acceso a un archivo de código.|

|**Opción**|**Descripción**|
|----------------| - |
|**/indexingStatus**|Muestra el estado y la configuración del servicio de indización de código.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: Inicia la indexación de todos los conjuntos de cambios.<br />-   **off**: Detiene la indexación de todos los conjuntos de cambios.<br />-   **keepupOnly**: Detiene la indexación de los conjuntos de cambios creados previamente e inicia solamente la de nuevos conjuntos de cambios.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Puede usar el carácter comodín (*) al principio, al final o en ambos extremos de la ruta de acceso del servidor.|Especifica una lista de archivos de código, con sus rutas de acceso, que no desea que estén indizados.<br /><br /> -   **add**: Agrega el archivo que no se quiere indexar a la lista de archivos omitidos.<br />-   **remove**: Quita el archivo que se quiere indexar de la lista de archivos omitidos.<br />-   **removeAll**: Borra la lista de archivos omitidos e inicia la indexación de todos los archivos.<br />-   **view**: Permite ver todos los archivos que no se están indexando.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Muestra el número especificado de archivos que supera el tamaño especificado en KB. Posteriormente, puede usar la opción **/ignoreList** para excluir estos archivos de la indexación.|
|**/reindexAll**|Borra datos anteriormente indizados y reinicia la indización.|
|**/destroyCodeIndex [/noPrompt]**|Elimina el índice de código y quita todos los datos indizados. No requiere confirmación si usa la opción **/noPrompt**.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Controla la cantidad de datos temporales creados por CodeLens al procesar los conjuntos de cambios. El límite predeterminado es de 2 GB.<br /><br /> -   **view**: Muestra el límite de tamaño actual.<br />-   `SizeInGBs`: Cambia el límite de tamaño.<br />-   **disable**: Quita el límite de tamaño.<br /><br /> Este límite se comprueba antes de que CodeLens procese un conjunto de cambios nuevo. Si los datos temporales superan este límite, CodeLens se pausará al procesar los conjuntos de cambios antiguos, pero no los nuevos. CodeLens comenzará a procesar de nuevo cuando los datos se hayan limpiado y no superen este límite. La limpieza se ejecuta automáticamente una vez al día. Esto significa que los datos temporales podrían superar este límite hasta que empiece a ejecutarse la limpieza.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Controla durante cuánto tiempo se indizará el historial de cambios. Esto afecta a la cantidad de historial mostrado por CodeLens. El límite predeterminado son 12 meses. Esto significa que CodeLens solo muestra el historial de cambios de los últimos 12 meses.<br /><br /> -   **view**: Muestra el número actual de meses.<br />-   **all**: Indexa todo el historial de cambios.<br />-   `NumberOfMonths`: Cambia el número de meses usados para indexar el historial de cambios.|
|**/collectionName:** `CollectionName`|Especifica el nombre de la colección de proyectos en la que se va a ejecutar el comando **CodeIndex**. Es obligatorio si no usa **/CollectionId**.|
|**/collectionId:** `CollectionId`|Especifica el número de identificación de la colección de proyectos en la que se va a ejecutar el comando **CodeIndex**. Es obligatorio si no usa **/CollectionName**.|

## <a name="examples"></a>Ejemplos

> [!NOTE]
> Las empresas, las organizaciones, los productos, los nombres de dominio, las direcciones de correo electrónico, los logotipos, los usuarios, las ubicaciones y los eventos que se citan a modo de ejemplo son ficticios.  No se pretende indicar, ni debe deducirse, ninguna asociación con compañías, organizaciones, productos, dominios, direcciones de correo electrónico, logotipos, personas, lugares o hechos reales.

 Para ver el estado y la configuración de la indización de código:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

 Para iniciar la indización de todos los conjuntos de cambios:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

 Para detener la indización de los conjuntos de cambios creados previamente e iniciar solo la indización de nuevos conjuntos de cambios:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

 Para buscar hasta 50 archivos de más de 10 KB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

 Para excluir un archivo concreto de la indización y agregarlo a la lista de archivos omitidos:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

 Para ver todos los archivos que no están indizados:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

 Para borrar datos indizados previamente y reiniciar la indización:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

 Para guardar todo el historial del conjunto de cambios:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

 Para quitar el límite de tamaño de los datos temporales de CodeLens y seguir indexando independientemente del tamaño de los datos temporales:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

 Para eliminar el índice de código con confirmación:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Vea también

- [Buscar cambios en el código y otro historial con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Managing server configuration with TFSConfig](/tfs/server/ref/command-line/tfsconfig-cmd) (Administración de la configuración del servidor con TFSConfig)