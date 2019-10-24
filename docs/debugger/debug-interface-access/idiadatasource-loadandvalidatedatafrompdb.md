---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97afff946827c37ec2f84457016525377977dc8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745002"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Abre y comprueba que el archivo de base de datos de programa (. pdb) coincide con la información de firma proporcionada y prepara el archivo. pdb como un origen de datos de depuración.

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

de Ruta de acceso al archivo. pdb.

`pcsig70`

de Firma GUID que se va a comprobar con la firma del archivo. pdb. Solo los archivos. pdb de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y versiones posteriores tienen firmas GUID.

`sig`

de Firma de 32 bits que se va a comprobar con la firma del archivo. pdb.

`age`

de Valor de edad que se va a comprobar. La antigüedad no se corresponde necesariamente con ningún valor de tiempo conocido, sino que se usa para determinar si un archivo. pdb no está sincronizado con un archivo. exe correspondiente.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_PDB_NOT_FOUND|No se pudo abrir el archivo o el archivo tiene un formato no válido.|
|E_PDB_FORMAT|Se intentó obtener acceso a un archivo con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma no coincide.|
|E_PDB_INVALID_AGE|Age no coincide.|
|E_INVALIDARG|Parámetro no válido.|
|E_UNEXPECTED|Ya se ha preparado el origen de datos.|

## <a name="remarks"></a>Comentarios
Un archivo. pdb contiene los valores de la firma y la edad. Estos valores se replican en el archivo. exe o. dll que coincide con el archivo. pdb. Antes de preparar el origen de datos, este método comprueba que la firma y la duración del archivo. pdb con nombre coinciden con los valores proporcionados.

Para cargar un archivo. pdb sin validación, use el método [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Para obtener acceso al proceso de carga de datos (a través de un mecanismo de devolución de llamada), use el método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Para cargar un archivo. pdb directamente desde la memoria, use el método [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
