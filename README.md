# KDB File Decryptor with LFSR-Based Encryption

This project is a Java-based **KDB File Decryptor** designed to decrypt a specific **KeePass Database (KDB)** file format, compatible only with the provided file, `store.kdb`. This file includes a unique encryption layer that requires the specific LFSR-based decryption implemented in this project. **Other KDB formats are not supported**.

> **Note**: This project was created as part of a take-home project for an interview, with a set of instructions on how a KDB file is structured, along with the example file `store.kdb` to decrypt.

## Project Overview

The purpose of this project is to decrypt a sample KDB file (KeePass Database file) provided as `store.kdb`, which includes a particular encryption format that differs from standard KDB files. This project exclusively supports the provided `store.kdb` file and will not work on other KDB formats.

## How to Use

To run this project:
1. Ensure you have **Java** installed.
2. Download the files in this repository and place them in a single directory.
3. Compile each Java file in this directory.
4. Follow the prompted instructions and insert the file path to load and decrypt `store.kdb`.

### Important Notes

- **KDB Compatibility**: This decryption process only applies to `store.kdb`, provided as an example. Any other KDB files will not be compatible due to format differences.
- **KeePass Database**: KDB files are traditionally used for securely storing passwords and sensitive information. The provided file, `store.kdb`, includes an additional encryption layer unique to this task.

## Files and Descriptions

### `BinaryDecryptor.java`
The `BinaryDecryptor` class contains the core decryption algorithm, utilizing an LFSR-based approach to decode binary data within `store.kdb`. This file implements the essential decryption logic, converting encrypted binary data into a readable format following the unique structure of the provided KDB file.

### `Block.java`
The `Block` class defines data blocks within `store.kdb`. Each block represents a segment of data, enabling the decryption algorithm to operate on a block-by-block basis. This modular approach is critical for managing and decrypting data efficiently.

### `Entry.java`
The `Entry` class represents individual entries within `store.kdb`. In KeePass databases, each entry typically holds specific data, such as credentials. This class structures each decrypted entry, making it readable after decryption.

### `InvalidFormatException.java`
`InvalidFormatException` is a custom exception that is thrown when the KDB file format does not match the expected structure of `store.kdb`. This ensures that only files matching the format of `store.kdb` are processed, preventing attempts to decrypt unsupported files.

### `KDBFileDecryptor.java`
The `KDBFileDecryptor` class is the primary interface for decrypting `store.kdb`. This file:
- Loads `store.kdb`.
- Uses `BinaryDecryptor` to decrypt each data block.
- Structures the decrypted data into entries with `Entry`.

This class manages the complete decryption process from file loading to data output.

### `KDBFileParser.java`
The `KDBFileParser` class interprets the structure of `store.kdb`, identifying and organizing data blocks and entries. It collaborates with the `Block` and `Entry` classes to ensure accurate data parsing, which is essential for feeding the decrypted data into the decryption process.
