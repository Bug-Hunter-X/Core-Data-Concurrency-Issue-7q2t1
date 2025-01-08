# Objective-C Core Data Concurrency Bug

This repository demonstrates a common issue in Objective-C Core Data programming: attempting to access and modify an `NSManagedObjectContext` from multiple threads without proper synchronization.  The `BuggyCoreData.m` file shows the problematic code, resulting in crashes or inconsistent data. The corrected implementation is provided in `FixedCoreData.m`, illustrating thread safety best practices using performBlockAndWait or proper background contexts.

## Bug Description
The bug stems from directly accessing and modifying the main context from a background thread.  Core Data's contexts are not thread-safe, leading to race conditions and data corruption. This often manifests as crashes with exceptions relating to Core Data or unpredictable database state.