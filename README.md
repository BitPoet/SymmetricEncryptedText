# SymmetricEncryptedText
ProcessWire module - symmetric encryption for text based fields

# Status
Alpha, proof-of-concept

# Requires
ProcessWire 3

# Description
This module adds an encryption option to all text fields (and those derived from FieldtypeText).

Field contents are encrypted using a symmetric key when a page is saved and decrypted when loaded from the database.

The module by default uses sodium (if loaded) in PHP versions >= 7.2, otherwise it falls back to the bundled [phpseclib](https://github.com/phpseclib/phpseclib).

Multi-Language fiels are supported too.

# WARNING!

Setting a field to encrypted and saving values in those fields is a one-way road!

Once encrypted, the contents cannot be unencrypted without writing a program to do so. Disabling the encryption option on a field after the fact gets you encrypted "garbage".

# Usage
- Download the zipped module through the [green button](https://github.com/BitPoet/SymmetricEncryptedText/archive/master.zip) at the top right of the GitHub repo or from the official PW module repository
- Extract in its own directory under site/modules.
- In the backend, click "Modules" -> "Refresh", then install "Symmetric Encryption for Text Fields".
- Go to module settings. An appropriately sized, random key will be generated if this is your first use.
- Copy the supplied entry into site/config.php
- Add fields or configure already present fields. On the "Details" tab you can enable encryption for the field in question
- Edit a page with such a field, enter a value there, save and enjoy

Existing, unencrypted values are left untouched until a new value is saved. That way, you can do a smooth upgrade
to encryption, but you have to save all pre-populated pages to have their values encrypted in the database.
Thus it is recommended to avoid adding encryption to already populated fields.

# Advanced Usage
You can hook after SymmetricEncryptedText::loadKey to retrieve your key from somewhere else, e.g. a different server.

# License
See LICENSE file in the toplevel directory

# Warning
Use at your own risk.
