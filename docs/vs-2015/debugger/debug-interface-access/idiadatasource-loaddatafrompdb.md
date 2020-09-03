---
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60b842e90c12d9a0bf07672380d24c8bacf71407
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198614"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre y prepara un archivo de base de datos de programa (. pdb) como un origen de datos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pdbPath  
 de Ruta de acceso al archivo. pdb.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.  
  
|Value|Descripción|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|No se pudo abrir el archivo o se determinó que el archivo tiene un formato no válido.|  
|E_PDB_FORMAT|Se intentó obtener acceso a un archivo con un formato obsoleto.|  
|E_INVALIDARG|Parámetro no válido.|  
|E_UNEXPECTED|El origen de datos ya se ha preparado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método carga los datos de depuración directamente desde un archivo. pdb.  
  
 Para validar el archivo. pdb con criterios concretos, use el método [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Para obtener acceso al proceso de carga de datos (a través de un mecanismo de devolución de llamada), use el método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Para cargar un archivo. pdb directamente desde la memoria, use el método [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
