<template>
    <div class = "backdrop" @click="closeModal">
        <div class = "modal" :class="{ sale: theme === 'sale'}">
            <slot> default content (if no slot passed in ) </slot>
            <div class="actions">
                <slot name = "links"></slot>
            </div> 
            <h1> {{ header }} </h1>
            <p> {{ text }} </p>
        </div>

    </div>

</template>
<script>
export default{
 
    props: ['header','text','theme'],
    methods: {
        closeModal(){
            this.$emit('close')
        }
    }
}
</script>

<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 200px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }
  .modal h1 {
    color: #03cfb4;
    border: none;
    padding: 0;
  }
  .modal p {
    font-style: normal;
  }
  /* sale styles */
  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
  .modal .actions a {
      color: #333;
      padding: 8px;
      border: 1px solid #eee;
      border-radius: 4px;
      text-decoration: none;
      margin: 10px;
  }
</style>