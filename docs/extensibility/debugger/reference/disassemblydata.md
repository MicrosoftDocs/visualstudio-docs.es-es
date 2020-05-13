---
title: DesensambladoDatos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737283"
---
# <a name="disassemblydata"></a>DisassemblyData
Describe una instrucción de desensamblado para el entorno de desarrollo integrado (IDE) que se va a mostrar.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Miembros
`dwFields`\
La [constante DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que especifica qué campos se rellenan.

`bstrAddress`\
La dirección como un desplazamiento desde algún punto de partida (normalmente el principio de la función asociada).

`bstrCodeBytes`\
Los bytes de código de esta instrucción.

`bstrOpcode`\
El código de operación para esta instrucción.

`bstrOperands`\
Los operandos de esta instrucción.

`bstrSymbol`\
El nombre del símbolo, si existe, asociado a la dirección (símbolo público, etiqueta, etc.).

`uCodeLocationId`\
Identificador de ubicación de código para esta línea desensamblada. Si la dirección de contexto de código de una línea es mayor que la dirección de contexto de código de otra, el identificador de ubicación de código desensamblado de la primera también será mayor que el identificador de ubicación de código de la segunda.

`posBeg`\
El [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición en un documento donde comienzan los datos de desensamblado.

`posEnd`\
El [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición en un documento donde finalizan los datos de desensamblado.

`bstrDocumentUrl`\
Para los documentos de texto que `bstrDocumentUrl` se pueden representar como nombres de archivo, el campo `file://file name`se rellena con el nombre de archivo donde se puede encontrar el origen, utilizando el formato .

Para los documentos de texto que `bstrDocumentUrl` no se pueden representar como nombres de archivo, es un identificador único para el documento y el motor de depuración debe implementar el [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) método.

Este campo también puede contener información adicional sobre sumas de comprobación. Para obtener información detallada, vea la sección Comentarios de.

`dwByteOffset`\
El número de bytes que la instrucción es desde el principio de la línea de código.

`dwFlags`\
La constante [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) que especifica qué indicadores están activos.

## <a name="remarks"></a>Observaciones
Cada `DisassemblyData` estructura describe una instrucción de desmontaje. Una matriz de estas estructuras se devuelve desde el [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.

La estructura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) se utiliza únicamente para documentos basados en texto. El intervalo de códigos fuente de esta instrucción se rellena solo para la `dwByteOffset == 0`primera instrucción generada a partir de una instrucción o línea, por ejemplo, cuando .

Para los documentos que no son textuales, se puede `bstrDocumentUrl` obtener un contexto de documento del código y el campo debe ser un valor nulo. Si `bstrDocumentUrl` el campo es `bstrDocumentUrl` el mismo `DisassemblyData` que el campo `bstrDocumentUrl` del elemento de matriz anterior, establezca el valor nulo.

Si `dwFlags` el campo `DF_DOCUMENT_CHECKSUM` tiene el indicador establecido, la información adicional `bstrDocumentUrl` de suma de comprobación sigue la cadena a la que apunta el campo. Específicamente, después del terminador de cadena nulo, sigue un GUID que identifica el algoritmo de suma de comprobación que a su vez va seguido de un valor de 4 bytes que indica el número de bytes en la suma de comprobación y que, a su vez, va seguido de los bytes de suma de comprobación. Consulte el ejemplo de este tema sobre cómo codificar [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]y descodificar este campo en .

## <a name="example"></a>Ejemplo
El `bstrDocumentUrl` campo puede contener información adicional `DF_DOCUMENT_CHECKSUM` que no sea una cadena si se establece la marca. El proceso de creación y lectura [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]de esta cadena codificada es sencillo en . Sin [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]embargo, en , es otro asunto. Para aquellos que tienen curiosidad, en el ejemplo siguiente [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] se muestra una manera de [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]crear la cadena codificada y una manera de descodificar la cadena codificada en .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
