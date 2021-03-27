# oracle-dbms_crypto
Oracle DBMS_Crypto Package

<bold>DBMS_CRYPTO</bold> provides an interface to encrypt and decrypt stored data, and can be used in conjunction with PL/SQL programs running network communications. It provides support for several industry-standard encryption and hashing algorithms, including the Advanced Encryption Standard (AES) encryption algorithm. AES has been approved by the National Institute of Standards and Technology (NIST) to replace the Data Encryption Standard (DES).

### ENCRYPT Function
This function encrypts RAW data using a stream or block cipher with a user supplied key and optional IV (initialization vector).

Syntax
```
DBMS_CRYPTO.ENCRYPT(
   src IN RAW,
   typ IN PLS_INTEGER,
   key IN RAW,
   iv  IN RAW          DEFAULT NULL)
RETURN RAW;
```

### ENCRYPT Procedures
These procedures encrypt LOB data using a stream or block cipher with a user supplied key and optional IV (initialization vector).

Syntax

```
DBMS_CRYPTO.ENCRYPT(
   dst IN OUT NOCOPY BLOB,
   src IN            BLOB,
   typ IN            PLS_INTEGER,
   key IN            RAW,
   iv  IN            RAW          DEFAULT NULL);
```
or clob:
```
DBMS_CRYPTO.ENCRYPT(
   dst IN OUT NOCOPY BLOB,
   src IN            CLOB         CHARACTER SET ANY_CS,
   typ IN            PLS_INTEGER,
   key IN            RAW,
   iv  IN            RAW          DEFAULT NULL);
```

### DECRYPT Function
This function decrypts RAW data using a stream or block cipher with a user supplied key and optional IV (initialization vector).

Syntax
```
DBMS_CRYPTO.DECRYPT(
   src IN RAW,
   typ IN PLS_INTEGER,
   key IN RAW,
   iv  IN RAW DEFAULT NULL)
RETURN RAW;
```

### DECRYPT Procedures
These procedures decrypt LOB data using a stream or block cipher with a user supplied key and optional IV (initialization vector).

Syntax
```
DBMS_CRYPTO.DECRYPT(
   dst IN OUT NOCOPY BLOB,
   src IN            BLOB,
   typ IN            PLS_INTEGER,
   key IN            RAW,
   iv  IN            RAW          DEFAULT NULL);
```
or using clob:
```
DBMS_CRYPT.DECRYPT(
   dst IN OUT NOCOPY CLOB         CHARACTER SET ANY_CS,
   src IN            BLOB,
   typ IN            PLS_INTEGER,
   key IN            RAW,
   iv  IN            RAW          DEFAULT NULL);
```

### HASH Function
A one-way hash function takes a variable-length input string, the data, and converts it to a fixed-length (generally smaller) output string called a hash value. The hash value serves as a unique identifier (like a fingerprint) of the input data. You can use the hash value to verify whether data has been changed or not.

Note that a one-way hash function is a hash function that works in one direction. It is easy to compute a hash value from the input data, but it is hard to generate data that hashes to a particular value. Consequently, one-way hash functions work well to ensure data integrity. Refer to "When to Use Hash or Message Authentication Code (MAC) Functions" for more information about using one-way hash functions.

This function applies to data one of the supported cryptographic hash algorithms listed in Table 40-3.

Syntax
```
DBMS_CRYPTO.Hash (
   src IN RAW,
   typ IN PLS_INTEGER)
RETURN RAW;
```
or in blob:
```
DBMS_CRYPTO.Hash (
   src IN BLOB,
   typ IN PLS_INTEGER)
RETURN RAW;
```
or in clob:
```
DBMS_CRYPTO.Hash (
   src IN CLOB CHARACTER SET ANY_CS,
   typ IN PLS_INTEGER)
RETURN RAW;
```

### MAC Function
A Message Authentication Code, or MAC, is a key-dependent one-way hash function. MACs have the same properties as the one-way hash function described in "HASH Function", but they also include a key. Only someone with the identical key can verify the hash. Also refer to "When to Use Hash or Message Authentication Code (MAC) Functions" for more information about using MACs.

This function applies MAC algorithms to data to provide keyed message protection. See Table 40-4 for a list of MAC algorithms that have been defined for this package.

Syntax
```
DBMS_CRYPTO.MAC (
   src IN RAW,
   typ IN PLS_INTEGER,
   key IN RAW)
 RETURN RAW;
```
```
DBMS_CRYPTO.MAC (
   src IN BLOB,
   typ IN PLS_INTEGER
   key IN RAW)
 RETURN RAW;
```
```
DBMS_CRYPTO.MAC (
   src IN CLOB CHARACTER SET ANY_CS,
   typ IN PLS_INTEGER
   key IN RAW)
 RETURN RAW;
```

### RANDOMBYTES Function
This function returns a RAW value containing a cryptographically secure pseudo-random sequence of bytes, which can be used to generate random material for encryption keys. The RANDOMBYTES function is based on the RSA X9.31 PRNG (Pseudo-Random Number Generator).

Syntax
```
DBMS_CRYPTO.RANDOMBYTES (
   number_bytes IN POSITIVE)
 RETURN RAW;
```



Source from [this](https://docs.oracle.com/database/121/ARPLS/d_crypto.htm#ARPLS664)
