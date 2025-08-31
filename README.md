# Kampus - Sui Move Learning Project

A comprehensive Sui Move project for learning fundamental data types and concepts through a university campus management system.

## About

This project demonstrates various Sui Move programming concepts using a university campus theme. It includes modules for handling different data types (boolean, numbers, strings, vectors) and showcases how to create, manage, and interact with student data on the Sui blockchain.

## Project Structure

```
kampus/
├── Move.toml                    # Package configuration
├── sources/                     # Source code modules
│   ├── kampus.move             # Main module (placeholder)
│   ├── belajar_boolean.move    # Boolean operations with student status
│   ├── belajar_number.move     # Number operations with student data
│   ├── belajar_string.move     # String operations with student names
│   ├── belajar_vector.move     # Vector operations with student lists
│   └── data_mahasiswa_lengkap.move # Complete student data management
├── tests/                      # Test modules
│   └── kampus_tests.move       # Test cases
└── build/                      # Compiled bytecode (generated)
```

## Learning Modules

### 1. `belajar_boolean.move` - Boolean Operations
Learn boolean data types through student status management:
- **Struct**: `StatusMahasiswa` - Tracks student active/graduation status
- **Functions**:
  - `buat_status()` - Create new student status
  - `set_lulus()` - Mark student as graduated
  - `nonaktifkan()` - Deactivate student
  - `bisa_wisuda()` - Check graduation eligibility

### 2. `belajar_number.move` - Number Operations
Explore different number types with student academic data:
- **Struct**: `DataMahasiswa` - Student academic information
- **Number Types**: `u32` (NIM), `u8` (age), `u64` (total credits)
- **Functions**:
  - `buat_data_mahasiswa()` - Create student academic record
  - `tambah_sks()` - Add credit hours
  - `tambah_umur()` - Increment age

### 3. `belajar_string.move` - String Operations
Master string handling with student names:
- **Struct**: `Mahasiswa` - Basic student with name
- **Functions**:
  - `buat_mahasiswa()` - Create new student
  - `ubah_nama()` - Update student name
  - `get_nama()` - Retrieve student name

### 4. `belajar_vector.move` - Vector Operations
Learn vector manipulation with student lists:
- **Struct**: `DaftarMahasiswa` - Student registry using vectors
- **Functions**:
  - `buat_daftar_kosong()` - Create empty student list
  - `tambah_mahasiswa()` - Add student to list
  - `jumlah_mahasiswa()` - Get student count
  - `get_mahasiswa_ke()` - Get student by index
  - `apakah_kosong()` - Check if list is empty

### 5. `data_mahasiswa_lengkap.move` - Complete Student Management
Comprehensive student data with business logic:
- **Struct**: `Mahasiswa` - Complete student profile
- **Features**:
  - Full student registration
  - Course enrollment (credit tracking)
  - Graduation requirements (144 credits minimum)
  - Student information retrieval

## Getting Started

### Prerequisites
- [Sui CLI](https://docs.sui.io/build/install) installed
- Basic understanding of Move programming language

### Installation & Build

1. **Clone or navigate to the project directory**:
   ```bash
   cd d:\files\Workshop\sui-dev\day1\kampus
   ```

2. **Build the project**:
   ```bash
   sui move build
   ```

3. **Run tests**:
   ```bash
   sui move test
   ```

4. **Publish to Sui network**:
   ```bash
   sui client publish --skip-fetch-latest-git-deps
   ```

## Usage Examples

### Creating and Managing Student Status (Boolean)
```move
// Create student status
let status = buat_status(string::utf8(b"John Doe"), ctx);

// Graduate the student
set_lulus(&mut status);

// Check graduation eligibility
let eligible = bisa_wisuda(&status); // returns true
```

### Working with Student Academic Data (Numbers)
```move
// Create student academic record
let data = buat_data_mahasiswa(12345678, 20, ctx);

// Add courses
tambah_sks(&mut data, 24); // Add 24 credit hours

// Age the student
tambah_umur(&mut data); // Increment age by 1
```

### Managing Student Lists (Vectors)
```move
// Create student registry
let daftar = buat_daftar_kosong(ctx);

// Add students
tambah_mahasiswa(&mut daftar, string::utf8(b"Alice"), 11111111);
tambah_mahasiswa(&mut daftar, string::utf8(b"Bob"), 22222222);

// Get student count
let count = jumlah_mahasiswa(&daftar); // returns 2

// Retrieve specific student
let (nama, nim) = get_mahasiswa_ke(&daftar, 0); // Get first student
```

## Key Concepts Learned

- **Data Types**: Boolean, integers (u8, u32, u64), strings, vectors
- **Structs**: Creating custom data structures with `has key` ability
- **Object Model**: Using `UID` for unique object identification
- **Functions**: Public functions, mutable references, return values
- **Vector Operations**: Creating, adding, accessing, and querying vectors
- **Business Logic**: Implementing real-world rules (graduation requirements)
- **Resource Management**: Creating and managing objects on Sui blockchain

## Configuration

**Move.toml Configuration**:
- **Package**: kampus v1.0.0
- **Edition**: 2024.beta
- **Dependencies**: Sui Framework (testnet)
- **Address**: `kampus = "0x0"`

## Contributing

This is a learning project. Feel free to:
- Add more modules exploring other Move concepts
- Enhance existing functions with additional features
- Improve documentation and examples
- Add comprehensive test cases

## Resources

- [Sui Documentation](https://docs.sui.io/)
- [Move Language Reference](https://move-language.github.io/move/)
- [Sui Move Concepts](https://docs.sui.io/concepts/sui-move-concepts)
- [Move Coding Conventions](https://docs.sui.io/concepts/sui-move-concepts/conventions)

## License

This project is for educational purposes. Feel free to use and modify for learning Move programming on Sui.
