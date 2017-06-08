---
layout: post
title:  "getter/setter"
date:   2017-01-13 13:40:34 +0800
categories: iOS
---

[参考链接](http://stackoverflow.com/questions/21802069/explicit-getters-setters-for-properties-mrc)

####@property (nonatomic, retain) NSNumber *count;

	- (NSNumber *)count {
	    return _count;
	}
	
	- (void)setCount:(NSNumber *)count {
	    if (count != _count) {
	        id oldValue = _count;
	        _count = [count retain];
	        [oldValue release];
	    }
	}

####@property (nonatomic, copy) NSNumber *count;

	- (NSNumber *)count {
	    return _count;
	}
	
	- (void)setCount:(NSNumber *)count {
	    id oldValue = _count;
	    _count = [count copy]; // retains (+1)
	    [oldValue release];
	}
	
	
####@property (atomic, retain) NSNumber *count;

	- (NSNumber *)count {
	    NSNumber *count;
	    @synchronized(self) {
	        count = [_count retain]; // +1
	    }
	    return [count autorelease]; // delayed -1
	}
	
	- (void)setCount:(NSNumber *)count {
	    id oldValue;
	    @synchronized(self) {
	        oldValue = _count;
	        _count = [count retain];
	    }
	    [oldValue release];
	}
####@property (assign) NSNumber *count;

	- (NSNumber *)count {
	    NSNumber *count;
	    @synchronized(self) {
	        count = _count;
	    }
	    return count;
	}
	
	- (void)setCount:(NSNumber *)count {
	    @synchronized(self) {
	        _count = count;
	    }
	}
	
	