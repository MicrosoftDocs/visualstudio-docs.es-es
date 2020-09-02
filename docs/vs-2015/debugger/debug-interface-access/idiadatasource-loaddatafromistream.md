---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547460"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prepara los datos de depuración almacenados en un archivo de base de datos de programa (. pdb) al que se tiene acceso a través de un flujo de datos en memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pIStream  
 de <xref:IStream> Objeto que representa el flujo de datos que se va a utilizar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.  
  
|Value|Descripción|  
|-----------|-----------------|  
|E_PDB_FORMAT|Se intentó obtener acceso a un archivo con un formato obsoleto.|  
|E_INVALIDARG|Parámetro no válido.|  
|E_UNEXPECTED|El origen de datos ya se ha preparado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite obtener los datos de depuración de un archivo ejecutable de la memoria a través de un <xref:IStream> objeto.  
  
 Para cargar un archivo. pdb sin validación, use el método [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Para validar el archivo. pdb con criterios concretos, use el método [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Para obtener acceso al proceso de carga de datos (a través de un mecanismo de devolución de llamada), use el método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
