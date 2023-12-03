<script setup>
  import {ref, reactive} from "vue";
  import Button from "./component/Button.vue";

  let entering = ref('');
  let result = ref();

  let operationResult = reactive({ 
    firstNumber: 0, 
    mathOperation: null, 
    secondNumber: 0,
    gotSumm: false
  });

  let reg = /\/|\*|\+|-|=/

  function clickTobtn(e) {

    if(operationResult.gotSumm) {
        clear();
    }

    enteringFn(e.target.dataset.operation);
  }

  function enteringFn(data) {
    entering.value += data;
  }

  function clear() {
    entering.value = '';
    result.value = null;

    operationResult.gotSumm = false;
  }

  function summ() {
    operationResult.firstNumber = Number(entering.value.split(reg)[0]);
    operationResult.mathOperation = entering.value.toString().match(reg)[0];
    operationResult.secondNumber = Number(entering.value.split(reg)[1]);
    operationResult.gotSumm = true;
    console.log(operationResult);

    result.value = eval(`${operationResult.firstNumber} ${operationResult.mathOperation} ${operationResult.secondNumber}`);
  }
  
</script>
<template>
  <div class="mx-auto overflow-hidden mt-10 shadow-lg mb-2 bg-indigo-900 shadow-lg border rounded-lg lg:w-2/5 md:w-2/6 sm:w-2/6">
    <div class="">
      
      <div 
        id="entering"
        class="pt-16 p-5 pb-0 text-white text-right text-3xl bg-indigo-800 min-h-[120px]">{{entering}}</div>

      <div 
        id="result" 
        class="p-5 text-white text-right text-3xl bg-indigo-800">
        =
        <textarea class="text-orange-500" v-model="result" cols="39"></textarea>
    </div>
      
    <div class="flex items-stretch bg-indigo-900 h-24">
      <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
    
        <Button 
          @click="clear"
          :button-data="'C'"
          :button-class="`rounded-lg h-20 w-20 flex items-center bg-orange-500 justify-center shadow-lg border-2 border-indigo-700 hover:border-2 hover:border-gray-500 focus:outline-none`">
          C
        </Button>
      </div>
    
      <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold"></div>
    
      <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold"></div>
    
      <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
        <Button 
          @click="clickTobtn"
          :button-data="'÷'">
          ÷
        </Button>
      </div>
    </div>
      
      <div class="flex items-stretch bg-indigo-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'7'"
              >
              7
          </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">

          <Button 
              @click="clickTobtn"
              :button-data="'8'"
              >
              8
          </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'9'"
              >
              9
          </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">

          <Button 
            @click="clickTobtn"
            :button-data="'*'"
            >
            ×
          </Button>

        </div>
      </div>
            
      <div class="flex items-stretch bg-indigo-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'4'"
              >
              4
            </Button>

          </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'5'"
              >
              5
          </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'6'"
              >
              6
            </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
              @click="clickTobtn"
              :button-data="'-'"
              >
              -
            </Button>
        </div>
      </div>
            
      <div class="flex items-stretch bg-indigo-900 h-24">
          <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">          
            <Button 
              @click="clickTobtn"
              :button-data="'1'"
              >
              1
            </Button>
          </div>
        
          <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
            <Button 
              @click="clickTobtn"
              :button-data="'2'"
              >
              2
            </Button>
          
          </div>
        
          <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          
            <Button 
              @click="clickTobtn"
              :button-data="'3'"
              >
              3
            </Button>
          </div>
        
          <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
       
            <Button 
              @click="clickTobtn"
              :button-data="'+'"
              >
              +
            </Button>

          </div>
      </div>
            

      <div class="flex items-stretch bg-indigo-900 h-24 mb-4">        
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
            <Button 
              @click="clickTobtn"
              :button-data="'0'"
              >
              0
            </Button>
          </div>
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold"></div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
    
          <Button 
            @click="clickTobtn"
            :button-data="'.'"
            >
            . 
          </Button>
        </div>
      
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <Button 
            @click="summ"
            :button-data="'='"
            :button-class="`rounded-lg h-20 w-20 flex items-center bg-orange-500 justify-center shadow-lg border-2 border-indigo-700 hover:border-2 hover:border-gray-500 focus:outline-none`">
            =  
          </Button>
        </div>
      </div>
    </div>
  </div>
</template>
