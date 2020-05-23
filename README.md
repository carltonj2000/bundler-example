# Example Bundler

The code in this repository is based on the
[Ronen Amiel - Build Your Own Webpack](https://www.youtube.com/watch?v=Gc9-7PBqOC8)
video.

Install globally `js-beautify` and `cli-highlight`. Then run:

```bash
node bundler | js-beautify | highlight
```

```
(function(mapping) {
   function require(id) {
       const [fn, mapping] = mapping[id];

       function localRequire(relativePath) {
           return require(mapping[relativePath])
       }

       const module = {
           exports: {}
       };

       fn(localRequire, module, module.exports);

       return module.exports;
   }

   require(0);
})({
   0: [
       function(require, module, exports) {
           "use strict";

           var _message = _interopRequireDefault(require("./message.js"));

           function _interopRequireDefault(obj) {
               return obj && obj.__esModule ? obj : {
                   "default": obj
               };
           }

           console.log(_message["default"]);
       },
       {
           "./message.js": 1
       }
   ] 1: [
       function(require, module, exports) {
           "use strict";

           Object.defineProperty(exports, "__esModule", {
               value: true
           });
           exports["default"] = void 0;

           var _name = _interopRequireDefault(require("./name.js"));

           function _interopRequireDefault(obj) {
               return obj && obj.__esModule ? obj : {
                   "default": obj
               };
           }

           var _default = "hi ".concat(_name["default"]);

           exports["default"] = _default;
       },
       {
           "./name.js": 2
       }
   ] 2: [
       function(require, module, exports) {
           "use strict";

           Object.defineProperty(exports, "__esModule", {
               value: true
           });
           exports["default"] = void 0;
           var _default = "Carlton";
           exports["default"] = _default;
       },
       {}
   ]
});
```
