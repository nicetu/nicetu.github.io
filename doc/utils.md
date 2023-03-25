# 前端常用的方法

[查看tool.js](../tool.js)

```js
/**
 * 1. 将数字转换为中文大写金额
 * 2. 邮箱校验方法
 * 3. 手机号校验方法
 * 4. 身份证校验方法
 * 5. 将数字转换为千分符格式
 * 6. 中国企业社会统一信用代码校验方法
 * 7. 生成一个指定长度的随机串方法
 * 8. 清除指定名称的cookie
 * 9. 获取指定名称的cookie
 * 10. 获取url中指定参数的值
 * 11. 校验指定长度字符串只包含数字的方法
 * 12. 校验指定长度字符串只包含数字或者字符的方法
 * 13. 生成文件下载的方法
 * 14. 将图片转换为base64编码
 * 15. 将本地图片转换为base64编码
 * 16. 对数据进行gzip压缩
 * 17. 对数据进行gzip解压
 * 18. 两数相乘，确保精度不丢失
 * 19. 两数相除，确保精度不丢失
 * 20. 将数字保留指定位小数，不四舍五入
 * 21. 根据key获取多叉树的value
 * 22. 生成密码强度校验方法，至少支持数字、字母、特殊字符中的两种
 * 23. 网络图片格式校验方法
 * 24. 本地文件判断是否为图片格式的校验方法
 * 25. 判断中国身份中是否支持长期
 * 26. 生成格式化日期的方法
 * 27. 获取每个季度的最后一天并返回数组
 * 28. 将小数转换为bp
 * 29. 将bp转换为小数
 * 30. 将小数转为%
 * 31. 将百分数转换为小数
 * 32. 将手机号格式化为3 4 4的格式
 * 33. 将银行卡号格式化为每4个数字一个空格的格式
 * 34. 将手机号中间4位替换为*的方法
 * 35. 将姓名格式化为隐藏后两位的格式
 * 36. 将身份证号码格式化为隐藏中间8位的格式
 * 37. 生成隐藏社会统一信用代码中间8位的方法，并间隔4位显示
 * 38. 将千分符格式的数字转换为普通数字
 * 39. 生成Aes加密的方法
 * 40. 生成Aes解密的方法
 * 41. 判断两个对象是否相等
 * 42. 生成黄金分割查找算法
 * 43. 生成给定字段的排序算法
 * 44. 过滤非数字字符
 * 45. 过滤非数字或者字母的方法
 * 46. 过滤非中文的输入方法
 * 47. 过滤非金额的输入方法，支持负数
 * 48. 过滤非金额的输入方法，只支持正数
 * 49. 生成默认补充0的指定位数小数的方法
 * 50. 生成插入树节点的方法
 * 51. 生成删除树节点的方法
 * 52. 将树结构转为数组结构并返回数组
 */



/** 
 * 将数字转换为中文大写金额
 * @param {number} num - 需要转换的数字
 * @returns {string} 转换后的中文大写金额
 */
export function numToChinese(num) {
  if (typeof num !== 'number') {
    return '请输入数字'
  }
  if (num > 999999999999.99) {
    return '数字太大，无法转换'
  }
  if (num === 0) {
    return '零元整'
  }
  const digitToChinese = ['零', '壹', '贰', '叁', '肆', '伍', '陆', '柒', '捌', '玖']
  const units = ['元', '万', '亿']
  const numStr = num.toFixed(2)
  const [integerPart, decimalPart] = numStr.split('.')
  const integerPartReversed = integerPart.split('').reverse().join('')
  let result = ''
  for (let i = 0; i < integerPartReversed.length; i++) {
    const digit = parseInt(integerPartReversed[i])
    if (i === 0 && digit === 0) {
      result += '零'
    } else if (i === 4 && result && result[result.length - 1] !== '万' && digit === 0) {
      result += '万'
    } else if (i === 8 && result && result[result.length - 1] !== '亿' && digit === 0) {
      result += '亿'
    } else if (digit !== 0) {
      result += digitToChinese[digit] + units[Math.floor(i / 4)]
    }
    if (i === 3 && result[result.length - 1] !== '万' && digit !== 0) {
      result += '万'
    }
  }
  if (decimalPart) {
    for (let i = 0; i < decimalPart.length; i++) {
      const digit = parseInt(decimalPart[i])
      if (digit !== 0) {
        result += digitToChinese[digit] + (i === 0 ? '角' : '分')
      }
    }
  } else {
    result += '整'
  }
  return result.split('').reverse().join('')
}

/**
 * 邮箱校验方法
 * @param {string} email - 需要校验的邮箱
 * @returns {boolean} 是否为有效邮箱
 */
export function validateEmail(email) {
  const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  return emailRegex.test(email);
}
/**
 * 手机号校验方法
 * @param {string} phone - 需要校验的手机号
 * @returns {boolean} 是否为有效手机号
 */
export function validatePhone(phone) {
  const phoneRegex = /^1[3-9]\d{9}$/;
  return phoneRegex.test(phone);
}

/**
 * 身份证校验方法
 * @param {string} idCard - 需要校验的身份证号码
 * @returns {boolean} 是否为有效身份证号码
 */
export function validateIdCard(idCard) {
  const idCardRegex = /^[1-9]\d{5}(19|20)\d{2}(0[1-9]|1[0-2])(0[1-9]|[1-2]\d|3[0-1])\d{3}[\dX]$/;
  if (!idCardRegex.test(idCard)) {
    return false;
  }
  const weightFactors = [7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2];
  const checkCodeMap = ['1', '0', 'X', '9', '8', '7', '6', '5', '4', '3', '2'];
  const checkCode = idCard[17];
  let sum = 0;
  for (let i = 0; i < 17; i++) {
    sum += parseInt(idCard[i]) * weightFactors[i];
  }
  return checkCode === checkCodeMap[sum % 11];
}
/**
 * 将数字转换为千分符格式
 * @param {number} num - 需要转换的数字
 * @returns {string} 转换后的千分符格式
 */
export function numToThousands(num) {
  if (typeof num !== 'number') {
    return '请输入数字'
  }
  const numStr = num.toFixed(2)
  const [integerPart, decimalPart] = numStr.split('.')
  const integerPartReversed = integerPart.split('').reverse().join('')
  let result = ''
  for (let i = 0; i < integerPartReversed.length; i++) {
    const digit = parseInt(integerPartReversed[i])
    if (i !== 0 && i % 3 === 0) {
      result += ','
    }
    result += digit
  }
  return result.split('').reverse().join('') + (decimalPart ? '.' + decimalPart : '')
}

/**
 * 中国企业社会统一信用代码校验方法
 * @param {string} code - 需要校验的统一信用代码
 * @returns {boolean} 是否为有效统一信用代码
 */
export function validateUnifiedSocialCreditCode(code) {
  const codeRegex = /^[0-9A-Z]{18}$/;
  if (!codeRegex.test(code)) {
    return false;
  }
  const weights = [1, 3, 9, 27, 19, 26, 16, 17, 20, 29, 25, 13, 8, 24, 10, 30, 28];
  const codes = "0123456789ABCDEFGHJKLMNPQRTUWXY";
  let sum = 0;
  for (let i = 0; i < 17; i++) {
    const char = code[i];
    const index = codes.indexOf(char);
    sum += index * weights[i];
  }
  const checkCodeIndex = (31 - sum % 31) % 31;
  const checkCode = codes[checkCodeIndex];
  return checkCode === code[17];
}
/**
 * 生成一个指定长度的随机串方法
 * @param {number} length - 随机串的长度
 * @returns {string} 生成的随机串
 */
export function generateRandomString(length) {
  const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  let result = '';
  for (let i = 0; i < length; i++) {
    result += characters.charAt(Math.floor(Math.random() * characters.length));
  }
  return result;
}
/**
 * 清除指定名称的cookie
 * @param {string} name - 需要清除的cookie名称
 */
export function clearCookie(name) {
  document.cookie = name + '=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;';
}
/**
 * 获取指定名称的cookie
 * @param {string} name - 需要获取的cookie名称
 * @returns {string|null} 获取到的cookie值，如果不存在则返回null
 */
export function getCookie(name) {
  const cookieStr = document.cookie;
  const cookies = cookieStr.split(';');
  for (let i = 0; i < cookies.length; i++) {
    const cookie = cookies[i].trim();
    const [cookieName, cookieValue] = cookie.split('=');
    if (cookieName === name) {
      return cookieValue;
    }
  }
  return null;
}
/**
 * 获取url中指定参数的值
 * @param {string} name - 需要获取的参数名称
 * @returns {string|null} 获取到的参数值，如果不存在则返回null
 */
export function getUrlParam(name) {
  const search = window.location.search;
  const params = new URLSearchParams(search);
  return params.get(name);
}
/**
 * 校验指定长度字符串只包含数字的方法
 * @param {string} str - 需要校验的字符串
 * @param {number} length - 字符串的长度
 * @returns {boolean} 是否为指定长度的纯数字字符串
 */
export function validateNumberString(str, length) {
  const regex = new RegExp(`^[0-9]{${length}}$`);
  return regex.test(str);
}
/**
 * 校验指定长度字符串只包含数字或者字符的方法
 * @param {string} str - 需要校验的字符串
 * @param {number} length - 字符串的长度
 * @returns {boolean} 是否为指定长度的纯数字或字符字符串
 */
export function validateAlphanumericString(str, length) {
  const regex = new RegExp(`^[a-zA-Z0-9]{${length}}$`);
  return regex.test(str);
}
/**
 * 生成文件下载的方法
 * @param {string} fileName - 下载文件的名称
 * @param {string} content - 下载文件的内容
 */
export function downloadFile(fileName, content) {
  const blob = new Blob([content], { type: 'text/plain' });
  const url = URL.createObjectURL(blob);
  const link = document.createElement('a');
  link.href = url;
  link.download = fileName;
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
  URL.revokeObjectURL(url);
}
/**
 * 将图片转换为base64编码
 * @param {string} imgUrl - 图片的url地址
 * @returns {Promise<string>} 转换后的base64编码
 */
async export function imgToBase64(imgUrl) {
  const response = await fetch(imgUrl);
  const blob = await response.blob();
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.readAsDataURL(blob);
    reader.onloadend = () => {
      resolve(reader.result);
    };
    reader.onerror = reject;
  });
}
/**
 * 将本地图片转换为base64编码
 * @param {File} file - 本地图片文件
 * @returns {Promise<string>} 转换后的base64编码
 */
async export function localImgToBase64(file) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.readAsDataURL(file);
    reader.onloadend = () => {
      resolve(reader.result);
    };
    reader.onerror = reject;
  });
}
/**
 * 对数据进行gzip压缩
 * @param {string} data - 需要压缩的数据
 * @returns {Promise<Uint8Array>} 压缩后的数据
 */
async export function gzipCompress(data) {
  const encoder = new TextEncoder();
  const compressed = await window.pako.gzip(encoder.encode(data));
  return compressed;
}
/**
 * 对数据进行gzip解压
 * @param {Uint8Array} compressed - 需要解压的数据
 * @returns {Promise<string>} 解压后的数据
 */
async export function gzipDecompress(compressed) {
  const decompressed = await window.pako.ungzip(compressed);
  const decoder = new TextDecoder();
  return decoder.decode(decompressed);
}
/**
 * 两数相乘，确保精度不丢失
 * @param {number} num1 - 第一个数
 * @param {number} num2 - 第二个数
 * @returns {number} 两数相乘的结果
 */
export function multiply(num1, num2) {
  const num1Str = num1.toString();
  const num2Str = num2.toString();
  const num1Decimal = num1Str.indexOf('.') !== -1 ? num1Str.length - num1Str.indexOf('.') - 1 : 0;
  const num2Decimal = num2Str.indexOf('.') !== -1 ? num2Str.length - num2Str.indexOf('.') - 1 : 0;
  const decimal = num1Decimal + num2Decimal;
  const result = num1 * num2;
  return parseFloat(result.toFixed(decimal));
}
/**
 * 两数相除，确保精度不丢失
 * @param {number} num1 - 被除数
 * @param {number} num2 - 除数
 * @returns {number} 两数相除的结果
 */
export function divide(num1, num2) {
  const num1Str = num1.toString();
  const num2Str = num2.toString();
  const num1Decimal = num1Str.indexOf('.') !== -1 ? num1Str.length - num1Str.indexOf('.') - 1 : 0;
  const num2Decimal = num2Str.indexOf('.') !== -1 ? num2Str.length - num2Str.indexOf('.') - 1 : 0;
  const decimal = Math.max(num1Decimal, num2Decimal);
  const result = num1 / num2;
  return parseFloat(result.toFixed(decimal));
}
/**
 * 将数字保留指定位小数，不四舍五入
 * @param {number} num - 需要处理的数字
 * @param {number} decimal - 保留的小数位数
 * @returns {number} 处理后的数字
 */
export function keepDecimal(num, decimal) {
  const power = Math.pow(10, decimal);
  return Math.floor(num * power) / power;
}
/**
 * 根据key获取多叉树的value
 * @param {object} tree - 多叉树对象
 * @param {string} key - 需要获取的value对应的key
 * @returns {*} 获取到的value，如果不存在则返回null
 */
export function getTreeValueByKey(tree, key) {
  if (!tree || typeof tree !== 'object') {
    return null;
  }
  if (tree[key]) {
    return tree[key];
  }
  for (const child of Object.values(tree)) {
    const result = getTreeValueByKey(child, key);
    if (result !== null) {
      return result;
    }
  }
  return null;
}
/**
 * 生成密码强度校验方法，至少支持数字、字母、特殊字符中的两种
 * @param {string} password - 需要校验的密码
 * @returns {boolean} 是否为强密码
 */
export function validatePassword(password) {
  const regex = /^(?=.*[0-9])(?=.*[a-zA-Z])(?=.*[!@#$%^&*])[0-9a-zA-Z!@#$%^&*]{8,}$/;
  return regex.test(password);
}
/**
 * 网络图片格式校验方法
 * @param {string} imgUrl - 图片的url地址
 * @returns {Promise<boolean>} 是否为有效图片格式
 */
async export function validateImageFormat(imgUrl) {
  const response = await fetch(imgUrl);
  const blob = await response.blob();
  const fileReader = new FileReader();
  return new Promise((resolve, reject) => {
    fileReader.onloadend = () => {
      const arr = (new Uint8Array(fileReader.result)).subarray(0, 4);
      let header = "";
      for (let i = 0; i < arr.length; i++) {
        header += arr[i].toString(16);
      }
      resolve(header === "89504e47" || header === "ffd8ffe0" || header === "ffd8ffe1" || header === "ffd8ffe2" || header === "ffd8ffe3" || header === "ffd8ffe8");
    };
    fileReader.onerror = reject;
    fileReader.readAsArrayBuffer(blob);
  });
}
/**
 * 本地文件判断是否为图片格式的校验方法
 * @param {File} file - 本地文件
 * @returns {Promise<boolean>} 是否为有效图片格式
 */
async export function validateLocalImageFormat(file) {
  const fileReader = new FileReader();
  return new Promise((resolve, reject) => {
    fileReader.onloadend = () => {
      const arr = (new Uint8Array(fileReader.result)).subarray(0, 4);
      let header = "";
      for (let i = 0; i < arr.length; i++) {
        header += arr[i].toString(16);
      }
      resolve(header === "89504e47" || header === "ffd8ffe0" || header === "ffd8ffe1" || header === "ffd8ffe2" || header === "ffd8ffe3" || header === "ffd8ffe8");
    };
    fileReader.onerror = reject;
    fileReader.readAsArrayBuffer(file);
  });
}
/**
 * 判断中国身份中是否支持长期
 * @param {string} idCard - 需要判断的身份证号码
 * @returns {boolean} 是否支持长期
 */
export function supportLongTerm(idCard) {
  const idCardRegex = /^[1-9]\d{5}(19|20)\d{2}(0[1-9]|1[0-2])(0[1-9]|[1-2]\d|3[0-1])(\d{3})(\d|X)$/;
  if (!idCardRegex.test(idCard)) {
    return false;
  }
  const year = parseInt(idCard.substr(6, 4));
  const month = parseInt(idCard.substr(10, 2));
  const day = parseInt(idCard.substr(12, 2));
  const birthday = new Date(year, month - 1, day);
  const now = new Date();
  const age = now.getFullYear() - year;
  if (now < new Date(now.getFullYear(), month - 1, day)) {
    age--;
  }
  if (age < 16) {
    return false;
  }
  if (idCard.substr(16, 1) === 'X') {
    return age >= 60;
  }
  const sex = parseInt(idCard.substr(16, 1)) % 2 === 1 ? 'M' : 'F';
  if (age < 18) {
    return false;
  }
  if (age === 18) {
    return sex === 'M';
  }
  if (age < 25) {
    return true;
  }
  if (age > 25 && age < 45) {
    return sex === 'F';
  }
  if (age > 45 && age < 60) {
    return true;
  }
  if (age >= 60) {
    return true;
  }
}
/**
 * 生成格式化日期的方法
 * @param {Date} date - 需要格式化的日期对象
 * @param {string} format - 格式化字符串，例如'yyyy-MM-dd HH:mm:ss'
 * @returns {string} 格式化后的日期字符串
 */
export function formatDate(date, format) {
  const year = date.getFullYear();
  const month = date.getMonth() + 1;
  const day = date.getDate();
  const hour = date.getHours();
  const minute = date.getMinutes();
  const second = date.getSeconds();
  const padZero = (num) => {
    return num < 10 ? '0' + num : num;
  }
  return format.replace('yyyy', year)
    .replace('MM', padZero(month))
    .replace('dd', padZero(day))
    .replace('HH', padZero(hour))
    .replace('mm', padZero(minute))
    .replace('ss', padZero(second));
}
/**
 * 获取每个季度的最后一天并返回数组
 * @param {number} year - 年份
 * @returns {Array} 包含每个季度最后一天的数组，格式为'yyyy-MM-dd'
 */
export function getLastDayOfQuarter(year) {
  const result = [];
  for (let i = 1; i <= 4; i++) {
    const month = i * 3;
    const lastDay = new Date(year, month, 0).getDate();
    const formattedDate = formatDate(new Date(year, month - 1, lastDay), 'yyyy-MM-dd');
    result.push(formattedDate);
  }
  return result;
}
/**
 * 将小数转换为bp
 * @param {number} num - 需要转换的小数
 * @returns {number} 转换后的bp值
 */
export function decimalToBp(num) {
  return num * 10000;
}
/**
 * 将bp转换为小数
 * @param {number} num - 需要转换的bp值
 * @returns {number} 转换后的小数
 */
export function bpToDecimal(num) {
  return num / 10000;
}
/**
 * 将小数转为%
 * @param {number} num - 需要转换的小数
 * @returns {string} 转换后的百分数
 */
export function decimalToPercent(num) {
  return (num * 100).toFixed(2) + '%';
}
/**
 * 将百分数转换为小数
 * @param {string} percent - 需要转换的百分数，例如'50%'
 * @returns {number} 转换后的小数，例如0.5
 */
export function percentToDecimal(percent) {
  const percentRegex = /^\d+(\.\d+)?%$/;
  if (!percentRegex.test(percent)) {
    return NaN;
  }
  return parseFloat(percent) / 100;
}
/**
 * 将手机号格式化为3 4 4的格式
 * @param {string} phone - 需要格式化的手机号
 * @returns {string} 格式化后的手机号
 */
export function formatPhone(phone) {
  const phoneRegex = /^1[3-9]\d{9}$/;
  if (!phoneRegex.test(phone)) {
    return '无效手机号';
  }
  return phone.replace(/(\d{3})(\d{4})(\d{4})/, '$1 $2 $3');
}
/**
 * 将银行卡号格式化为每4个数字一个空格的格式
 * @param {string} cardNumber - 需要格式化的银行卡号
 * @returns {string} 格式化后的银行卡号
 */
export function formatCardNumber(cardNumber) {
  const regex = /(\d{4})(?=\d)/g;
  return cardNumber.replace(regex, '$1 ');
}
/**
 * 将手机号中间4位替换为*的方法
 * @param {string} phone - 需要替换的手机号
 * @returns {string} 替换后的手机号
 */
export function hidePhoneMiddle(phone) {
  const phoneRegex = /^1[3-9]\d{9}$/;
  if (!phoneRegex.test(phone)) {
    return '无效手机号';
  }
  return phone.replace(/(\d{3})\d{4}(\d{4})/, '$1****$2');
}
/**
 * 将姓名格式化为隐藏后两位的格式
 * @param {string} name - 需要格式化的姓名
 * @returns {string} 格式化后的姓名
 */
export function hideNameLastTwo(name) {
  if (name.length <= 2) {
    return '*'.repeat(name.length);
  }
  const lastTwo = name.substr(-2);
  return '*'.repeat(name.length - 2) + lastTwo;
}
/**
 * 将身份证号码格式化为隐藏中间8位的格式
 * @param {string} idCard - 需要格式化的身份证号码
 * @returns {string} 格式化后的身份证号码
 */
export function hideIdCardMiddle(idCard) {
  const idCardRegex = /^[1-9]\d{5}(19|20)\d{2}(0[1-9]|1[0-2])(0[1-9]|[1-2]\d|3[0-1])\d{3}[\dX]$/;
  if (!idCardRegex.test(idCard)) {
    return '无效身份证号码';
  }
  return idCard.replace(/(\d{6})\d{8}(\d{4})/, '$1********$2').replace(/(\d{4})/g, '$1 ');
}
/**
 * 生成隐藏社会统一信用代码中间8位的方法，并间隔4位显示
 * @param {string} code - 需要隐藏中间8位的统一信用代码
 * @returns {string} 隐藏中间8位后的统一信用代码
 */
export function hideUnifiedSocialCreditCodeMiddle(code) {
  const codeRegex = /^[0-9A-Z]{18}$/;
  if (!codeRegex.test(code)) {
    return '无效统一信用代码';
  }
  return code.replace(/(\w{8})\w{8}(\w{2})/, '$1********$2').replace(/(\w{4})/g, '$1 ');
}
/**
 * 将千分符格式的数字转换为普通数字
 * @param {string} str - 需要转换的千分符格式数字
 * @returns {number} 转换后的普通数字
 */
export function removeThousands(str) {
  return parseFloat(str.replace(/,/g, ''));
}

/**
 * 生成Aes加密的方法
 * @param {string} data - 需要加密的数据
 * @param {string} key - 加密的密钥
 * @returns {string} 加密后的数据
 */
export function aesEncrypt(data, key) {
  const iv = CryptoJS.lib.WordArray.random(16);
  const encrypted = CryptoJS.AES.encrypt(data, CryptoJS.enc.Utf8.parse(key), {
    iv: iv,
    mode: CryptoJS.mode.CBC,
    padding: CryptoJS.pad.Pkcs7
  });
  return iv.concat(encrypted.ciphertext).toString(CryptoJS.enc.Base64);
}

/**
 * 生成Aes解密的方法
 * @param {string} data - 需要解密的数据
 * @param {string} key - 解密的密钥
 * @returns {string} 解密后的数据
 */
export function aesDecrypt(data, key) {
  const ciphertext = CryptoJS.enc.Base64.parse(data);
  const iv = ciphertext.clone();
  iv.sigBytes = 16;
  iv.clamp();
  ciphertext.words.splice(0, 4);
  ciphertext.sigBytes -= 16;
  const decrypted = CryptoJS.AES.decrypt({ ciphertext: ciphertext }, CryptoJS.enc.Utf8.parse(key), {
    iv: iv,
    mode: CryptoJS.mode.CBC,
    padding: CryptoJS.pad.Pkcs7
  });
  return decrypted.toString(CryptoJS.enc.Utf8);
}
/**
 * 判断两个对象是否相等
 * @param {object} obj1 - 第一个对象
 * @param {object} obj2 - 第二个对象
 * @returns {boolean} 是否相等
 */
export function isEqual(obj1, obj2) {
  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);
  if (keys1.length !== keys2.length) {
    return false;
  }
  for (const key of keys1) {
    const val1 = obj1[key];
    const val2 = obj2[key];
    const areObjects = isObject(val1) && isObject(val2);
    if (
      (areObjects && !isEqual(val1, val2)) ||
      (!areObjects && val1 !== val2)
    ) {
      return false;
    }
  }
  return true;
}
/**
 * 生成黄金分割查找算法
 * @param {Array} arr - 需要查找的有序数组
 * @param {number} target - 需要查找的目标值
 * @returns {number} 目标值在数组中的索引，如果不存在则返回-1
 */
export function goldenSectionSearch(arr, target) {
  const goldenRatio = (1 + Math.sqrt(5)) / 2;
  let left = 0;
  let right = arr.length - 1;
  while (left <= right) {
    const mid = Math.floor(left + (right - left) / goldenRatio);
    if (arr[mid] === target) {
      return mid;
    } else if (arr[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return -1;
}
/**
 * 生成给定字段的排序算法
 * @param {Array} arr - 需要排序的数组
 * @param {string} field - 排序的字段
 * @param {boolean} isAsc - 是否升序排序，默认为true
 * @returns {Array} 排序后的新数组
 */
export function sortByField(arr, field, isAsc = true) {
  const compare = (a, b) => {
    const valA = a[field];
    const valB = b[field];
    if (valA < valB) {
      return isAsc ? -1 : 1;
    } else if (valA > valB) {
      return isAsc ? 1 : -1;
    } else {
      return 0;
    }
  }
  return arr.slice().sort(compare);
}
/**
 * 过滤非数字字符
 * @param {string} str - 需要过滤的字符串
 * @returns {string} 过滤后的数字字符串
 */
export function filterNonNumeric(str) {
  return str.replace(/\D/g, '');
}
/**
 * 过滤非数字或者字母的方法
 * @param {string} str - 需要过滤的字符串
 * @returns {string} 过滤后的数字或字母字符串
 */
export function filterNonAlphanumeric(str) {
  return str.replace(/[^0-9a-zA-Z]/g, '');
}
/**
 * 过滤非中文的输入方法
 * @param {string} str - 需要过滤的字符串
 * @returns {string} 过滤后的中文字符串
 */
export function filterNonChinese(str) {
  return str.replace(/[^\u4e00-\u9fa5]/g, '');
}
/**
 * 过滤非金额的输入方法，支持负数
 * @param {string} str - 需要过滤的字符串
 * @returns {string} 过滤后的金额字符串
 */
export function filterNonAmount(str) {
  return str.replace(/[^\d.-]/g, '').replace(/^\./g, '').replace(/\.{2,}/g, '.').replace('.', '$#$').replace(/\./g, '').replace('$#$', '.');
}
/**
 * 过滤非金额的输入方法，只支持正数
 * @param {string} str - 需要过滤的字符串
 * @returns {string} 过滤后的金额字符串
 */
export function filterAmount(str) {
  return str.replace(/[^\d.]/g, '').replace(/^\./g, '').replace(/\.{2,}/g, '.').replace('.', '$#$').replace(/\./g, '').replace('$#$', '.');
}
/**
 * 生成默认补充0的指定位数小数的方法
 * @param {number} num - 需要处理的数字
 * @param {number} decimal - 保留的小数位数
 * @returns {string} 处理后的数字字符串
 */
export function formatDecimal(num, decimal) {
  const str = num.toFixed(decimal);
  const parts = str.split('.');
  if (parts.length === 1) {
    return str + '.' + '0'.repeat(decimal);
  } else {
    return parts[0] + '.' + parts[1].padEnd(decimal, '0');
  }
}
/**
 * 生成插入树节点的方法
 * @param {object} tree - 多叉树对象
 * @param {string} parentKey - 父节点的key
 * @param {object} newNode - 新节点对象
 * @returns {boolean} 是否成功插入节点
 */
export function insertTreeNode(tree, parentKey, newNode) {
  if (!tree || typeof tree !== 'object') {
    return false;
  }
  if (tree[parentKey]) {
    if (!tree[parentKey].children) {
      tree[parentKey].children = {};
    }
    tree[parentKey].children[newNode.key] = newNode;
    return true;
  }
  for (const child of Object.values(tree)) {
    const result = insertTreeNode(child, parentKey, newNode);
    if (result) {
      return true;
    }
  }
  return false;
}
/**
 * 生成删除树节点的方法
 * @param {object} tree - 多叉树对象
 * @param {string} key - 需要删除的节点的key
 * @returns {boolean} 是否成功删除节点
 */
export function deleteTreeNode(tree, key) {
  if (!tree || typeof tree !== 'object') {
    return false;
  }
  if (tree[key]) {
    delete tree[key];
    return true;
  }
  for (const childKey of Object.keys(tree)) {
    const child = tree[childKey];
    const result = deleteTreeNode(child.children, key);
    if (result) {
      if (Object.keys(child.children).length === 0) {
        delete child.children;
      }
      return true;
    }
  }
  return false;
}
/**
 * 将树结构转为数组结构并返回数组
 * @param {object} tree - 多叉树对象
 * @returns {Array} 转换后的数组
 */
export function treeToArray(tree) {
  const result = [];
  const traverse = (node) => {
    result.push(node);
    if (node.children) {
      for (const child of Object.values(node.children)) {
        traverse(child);
      }
    }
  }
  traverse(tree);
  return result;
}

```