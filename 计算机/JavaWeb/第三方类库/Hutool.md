对文件、流、加密解密、转码、正则、线程、XML等 JDK 方法进行封装




# 加密解密
>[!quote] 加密分类
>- **对称加密**
> 	- AES
> 	- ARCFOUR
> 	- Blowfish
> 	- DES
> 	- DESede
> 	- RC2
> 	- PBEWithMD5AndDES
> 	- PBEWithSHA1AndDESede
> 	- PBEWithSHA1AndRC2_40
> - **非对称加密**
> 	- RSA
> 	- DSA
> - **摘要加密**
> 	- MD2
> 	- MD5
> 	- SHA-1
> 	- SHA-256
> 	- SHA-384
> 	- SHA-512
> 	- HmacMD5
> 	- HmacSHA1
> 	- HmacSHA256
> 	- HmacSHA384
> 	- HmacSHA512

## 常见加密 SecureUtil
- 对称加密
	- `SecureUtil.aes`
	- `SecureUtil.des`
- 摘要加密
	- `SecureUtil.md5`
	- `SecureUtil.sha1`
	- `SecureUtil.hmac`
	- `SecureUtil.hmacMd5`
	- `SecureUtil.hmacSha1`
- 非对称加密
	- `SecureUtil.rsa`
	- `SecureUtil.dsa`
- UUID
	- `SecureUtil.simpleUUID` 方法提供无“-”的UUID
- 密钥生成
	- `SecureUtil.generateKey` 针对对称加密生成密钥
	- `SecureUtil.generateKeyPair` 生成密钥对（用于非对称加密）
	- `SecureUtil.generateSignature` 生成签名（用于非对称加密）






