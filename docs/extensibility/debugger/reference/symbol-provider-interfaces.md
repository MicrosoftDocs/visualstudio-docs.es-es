---
title: Interfaces de proveedor de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715851"
---
# <a name="symbol-provider-interfaces"></a>Interfaces de proveedor de símbolos
A continuación se muestran las interfaces de control de símbolos para [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Debate
 Estas interfaces se utilizan para evaluar las variables en una pila de llamadas durante el modo de interrupción. Solo se implementan para los proveedores de símbolos de Common Language Runtime (SP).

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Representa la dirección de un elemento.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Representa la dirección de un elemento, que proporciona acceso al identificador de proceso.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Representa un tipo de matriz o símbolo de matriz.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Representa un tipo de clase o símbolo de clase.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Representa un proveedor de símbolos COM+ con métodos que son específicos del código administrado.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Representa un proveedor de símbolos COM+ con métodos que son específicos del código administrado y extiende el **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Representa un símbolo o tipo que es un contenedor para otros símbolos o tipos.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Representa un atributo personalizado que se puede adjuntar a un símbolo.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Representa una consulta de atributos personalizados en un método o tipo.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Proporciona acceso a los atributos personalizados de un símbolo.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|La interfaz base para cualquier tipo que se pueda determinar en tiempo de ejecución.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Representa un campo dinámico para un objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Representa un tipo de enumeración.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Dañado|Extiende los tipos de campos disponibles para admitir los genéricos de código administrado.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|La clase base para todos los campos; representa una descripción de un símbolo o un tipo.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Representa la definición de un campo para un tipo genérico de código administrado.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Representa una instancia de un campo para un tipo genérico de código administrado.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Representa un parámetro para un tipo genérico de código administrado.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Representa un método.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Representa un modificador opcional Debug.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Representa un puntero.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Representa un valor de enumeración de tipo primitivo de una interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Representa una propiedad de una clase de código administrado que se puede obtener o establecer.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Representa un proveedor de símbolos que proporciona símbolos y tipos.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Representa un proveedor de símbolos con acceso directo a metadatos e interfaces de símbolos principales.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Representa la capacidad de crear un campo que representa un tipo.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Extiende el **IDebugTypeFieldBuilder** para poder crear tipos de matriz.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Representa una colección de objetos [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Representa una colección de objetos [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) .|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Representa una colección de objetos [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|

## <a name="see-also"></a>Consulte también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
