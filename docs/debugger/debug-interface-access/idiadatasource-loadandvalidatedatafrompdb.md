---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb140470e45f49806087941127638f56ce5d7150
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Se abre y comprueba que el archivo de programa (.pdb) de la base de datos coincide con la información de la firma proporcionada y prepara el archivo .pdb como un origen de datos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdbPath`  
 [in] La ruta de acceso al archivo .pdb.  
  
 `pcsig70`  
 [in] La firma GUID para comprobar con la firma del archivo PDB. Los archivos .pdb solo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y versiones posteriores tienen firmas GUID.  
  
 `sig`  
 [in] La firma de 32 bits para comprobar con la firma del archivo PDB.  
  
 `age`  
 [in] Valor de edad que se va a comprobar. La antigüedad no corresponden necesariamente a cualquier valor de tiempo conocido, que se usa para determinar si un archivo .pdb no está sincronizado con un archivo .exe correspondiente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|No se pudo abrir el archivo o el archivo tiene un formato no válido.|  
|E_PDB_FORMAT|Se ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E_PDB_INVALID_SIG|No coincide con la firma.|  
|E_PDB_INVALID_AGE|Antigüedad no coincide.|  
|E_INVALIDARG|Parámetro no válido.|  
|E_UNEXPECTED|Ya se ha preparado el origen de datos.|  
  
## <a name="remarks"></a>Comentarios  
 Un archivo .pdb contiene valores de firma y edad. Estos valores se replican en el archivo .exe o .dll que coincide con el archivo PDB. Antes de preparar el origen de datos, este método comprueba que firma el archivo .pdb con nombre y la edad coinciden con los valores proporcionados.  
  
 Para cargar un archivo .pdb sin validación, utilice la [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.  
  
 Para obtener acceso a los procesos de carga de datos (a través de un mecanismo de devolución de llamada), use la [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
 Para cargar un archivo .pdb directamente desde la memoria, utilice la [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) método.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)