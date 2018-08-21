一、 阶乘

闭包实现阶乘，由于内部arr存储了结果，效率会更高
var fn = (function () {
        var arr = [1, 1, 2]; // 第0位是占位，从第一位开始算起
        return function (n) {
            var res = arr[n]; // 因为内部引用了arr，并返回，导致arr一直在内存中
            if (res) {
                return res;
            } else {
                arr[n] = n * fn(n-1);
                return arr[n];
            }
        }
    })();
递归实现阶乘
function fn(n) {
        if (n == 1) {
            return 1;
        }else if (n == 2) {
            return 2;
        }
        return n * fn (n-1);
    }
递推实现阶乘
function fn1(n) {
        var x = 1,
            z = 1;
        if (n == 1) {
            return 1;
        }else if (n==2) {
            return 2;
        }else {
            for (var i = 0; i < n; i++) {
                z = z * x;
                x = ++x;
            }
        }
        return z;
    }
二、实现裴波那契

闭包实现裴波那契数列
var fn = (function () {
        var arr = [0, 1, 1]; // 第0位是占位，从第一位开始算起
        return function (n) {
            var res = arr[n]; // 因为内部引用了arr，并返回，导致arr一直在内存中
            if (res) {
                return res;
            } else {
                arr[n] = fn(n-1) + fn(n-2);
                return arr[n];
            }
        }
    })();
递归实现裴波那契
function fn(n) {
        if (n == 1 || n==2) {
            return 1;
        }
        return fn(n-1) + fn (n-2);
    }
递推法实现裴波那契
function fn1(n) {
        var x = 1,
            y = 1,
            z = 0;
        if (n == 1 || n == 2) {
            return 1;
        }else {
            for (var i = 2; i < n; i++) {
                z = x + y;
                x = y;
                y = z;
            }

        }
        return z;
    }