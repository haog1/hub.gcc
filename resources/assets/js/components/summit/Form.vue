<template>
    <div>
        <br><br><br>
        <section class="hero is-info is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title has-text-left" >
                        無可限量 | Limitless
                    </h1>
                    <h2 class="subtitle has-text-left">
                        2018 榮耀城領袖高峰會
                    </h2>
                </div>
            </div>
        </section>
        <div class="container">
            <div class="box">
                <p class="is-size-3">基本資料</p>
                <br>

                <div class="columns">
                    <!-- name -->
                    <div class="column" :class="{'has-error' : errors.has('first_name') }">
                        <label class="label" for="first_name">名 *</label>
                        <div>
                            <input style="width:80%" class="is-size-6" v-model="first_name"
                                   v-validate data-vv-rules="required|min:1|max:20" data-vv-as="名"
                                   id="first_name" placeholder="First Name" type="text" name="first_name" required>
                            <br>
                            <span class="help-block" v-show="errors.has('first_name')" style="color: red !important;">{{errors.first('first_name')}}</span>
                        </div>
                    </div>

                    <div class="column" :class="{'has-error' : errors.has('last_name') }">
                        <label class="label" for="last_name">姓 *</label>
                        <div>
                            <input style="width:80%" class="is-size-6" v-model="last_name"
                                   v-validate data-vv-rules="required|min:1|max:20" data-vv-as="姓"
                                   id="last_name" placeholder="Last Name" type="text" name="last_name" required>
                            <br>
                            <span class="help-block" v-show="errors.has('last_name')" style="color: red !important;">{{errors.first('last_name')}}</span>
                        </div>
                    </div>
                    <!-- gender -->
                    <div class="column"  :class="{ 'has-error': errors.has('gender') }">
                        <label class="label">性別 *</label>
                        <div class="field">
                            <label style="margin-right:20px;">
                                <input class="is-size-5" v-model="gender" v-validate="'required|in:male,female'" data-vv-as="性别"
                                       name="gender" value="male" id="gender" type="radio"> 男 <em class="fa fa-male" style="color: cornflowerblue"></em>
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="gender" name="gender" value="female" type="radio"> 女 <em class="fa fa-female" style="color: hotpink"></em>
                            </label>
                            <br>
                            <span class="help-block" v-show="errors.has('gender')" style="color: red !important;">{{ errors.first('gender') }}</span>
                        </div>
                    </div>
                </div>

                <div class="columns">
                    <!--mobile-->
                    <div class="column" :class="{'has-error' : errors.has('mobile') }">
                        <label class="label" for="mobile">電話號碼 *</label>
                        <div>
                            <input style="width:80%" class="is-size-6" v-model="mobile"
                                   v-validate data-vv-rules="required|numeric|min:10|max:25" data-vv-as="電話號碼"
                                   id="mobile" placeholder="Mobile Number, eg: 0400000000" type="text" name="mobile" required>
                            <br>
                            <span class="help-block" v-show="errors.has('mobile')" style="color: red !important;">{{errors.first('mobile')}}</span>
                        </div>
                    </div>
                    <!--first time?-->
                    <div class="column"  :class="{ 'has-error': errors.has('firstTime') }">
                        <label class="label">第一次參加 *</label>
                        <div class="field">
                            <label style="margin-right:20px;">
                                <input class="is-size-5" v-model="firstTime" v-validate="'required|in:yes,no'" data-vv-as="是否第一次參加"
                                       name="firstTime" value="yes" id="firstTime" type="radio"> 是 <em class="fa fa-check" style="color: cornflowerblue"></em>
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="firstTime" name="firstTime" value="no" type="radio">
                                否 <em class="fa fa-times" style="color: hotpink"></em>
                            </label>
                            <br>
                            <span class="help-block" v-show="errors.has('firstTime')" style="color: red !important;">{{ errors.first('firstTime') }}</span>
                        </div>
                    </div>

                </div>

                <!-- emails -->
                <p class="is-size-7" style="display:inline;color:#219ADB">備註:支付憑證將會發到您所填寫的郵箱</p>
                <div class="columns">
                    <div class="column" :class="{'has-error' : errors.has('email') }">
                        <label class="label" for="email">郵箱 * </label>
                        <div class="field">
                            <input style="width:80%" class="is-size-6" v-model="email"
                                   v-validate data-vv-rules="required|email|max:50" data-vv-as="郵箱"
                                   id="email" placeholder="Email Address" type="email" name="email" required>
                            <br>
                            <span class="help-block" v-show="errors.has('email')" style="color: red !important;">{{errors.first('email')}}</span>
                        </div>
                    </div>
                    <div class="column" :class="{'has-error' : errors.has('email-confirm') }">
                        <label class="label" for="email-confirm">確認郵箱 *</label>
                        <div class="field">
                            <input style="width:80%" class="is-size-6" v-model="email_confirm"
                                   id="email-confirm" placeholder="Confirm Email Address" v-validate data-vv-rules="required|email|confirmed:email|max:50" data-vv-as="確認郵箱"
                                   type="email" name="email-confirm" required>
                            <br>
                            <span class="help-block" v-show="errors.has('email-confirm')" style="color: red !important;">{{errors.first('email-confirm')}}</span>
                        </div>
                    </div>
                </div>

                <div class="columns">
                    <!--where know us-->
                    <div class="column" :class="{ 'has-error': errors.has('path') }">
                        <label class="label">從什麼途徑了解到我們 *</label>
                        <div class="control">
                            <label class="radio">
                                <input class="is-size-5" v-model="path" v-validate="{ rules: 'required|in:friend,classmate,colleague,web,social,family,other', args: 'path' }" data-vv-as="途径"
                                       name="path" value="friend" id="path" type="radio"> 朋友
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="path" name="path" value="classmate" type="radio"> 同學
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="path" name="path" value="colleague" type="radio"> 同事
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="path" name="path" value="social" type="radio"> 網路平台
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="path" name="path" value="family" type="radio"> 家人
                            </label>
                            <label class="radio">
                                <input class="is-size-5" v-model="path" name="path" value="other" type="radio"> 其他
                            </label>
                            <br>
                            <span class="help-block" v-show="errors.has('path')" style="color: red !important;">{{ errors.first('path') }}</span>
                        </div>
                    </div>
                    <!-- coupon -->
                    <div class="column" :class="{'has-error' : errors.has('coupon') }">
                        <label class="label" for="coupon">折扣券</label>
                        <div>
                            <input style="width:80%" class="is-size-6" v-model="coupon" id="coupon" placeholder="Enter your Discount Code here" type="text" name="coupon" required>
                            <span v-if="this.isDiscounted"><em class="fa fa-check fa-2x" style="color:cornflowerblue;"></em></span>
                            <span v-cloak v-show="!this.isDiscounted && this.coupon"><em class="fa fa-times fa-2x" style="color:red;"></em></span>
                            <br>
                            <span class="help-block" v-show="errors.has('coupon')" style="color: red !important;">{{errors.first('coupon')}}</span>
                        </div>
                    </div>

                </div>
            </div>

            <div class="field">
                <button class="button is-info" :disabled=" errors.any() || !complete" style="width:100%" @click.prevent="nextStep">
                    Proceed to checkout
                </button>
            </div>
        </div>
    </div>
</template>

<script>

    export default {

        data(){
            return {
                first_name: '',
                last_name: '',
                mobile: '',
                firstTime: '',
                gender: '',
                price: 99.00,
                email: '',
                email_confirm: '',
                path: '',
                coupon:'',
                isDiscounted: false
            }
        },

        updated() {
            if (this.coupon && this.email) {
                let vm = this;
                axios.post('/api/form/validate-coupon', {coupon:this.coupon, email: this.email}).then(response => {
                    vm.isDiscounted = response.data.message;
                    vm.price = response.data.price;
                }).catch(err =>{});
            }
        },


        computed:{
            complete(){
                return this.gender && this.firstTime &&
                    this.email.length > 0 && this.mobile.length >= 10 &&
                    this.email === this.email_confirm && this.path && this.first_name.length <= 20 && this.last_name.length <= 20 &&
                    this.email.length <= 50 && this.mobile.length <= 25;
            }
        },

        methods:{

            nextStep() {
                let vm = this;

                if (this.validatesInputLength()) {

                    this.$validator.validateAll().then(result => {

                        vm.$store.dispatch('paymentInfoRequest').then(response => {

                            vm.$router.push({
                                name: 'summit.checkout', params: {
                                    first_name: vm.first_name,
                                    last_name: vm.last_name,
                                    email: vm.email,
                                    firstTime: vm.firstTime,
                                    gender: vm.gender,
                                    mobile: vm.mobile,
                                    path: vm.path,
                                    isDiscounted: vm.isDiscounted,
                                    price: vm.price,
                                    coupon: vm.isDiscounted ? vm.coupon : 'null'
                                }
                            });

                        }).catch(error => {
                        });

                    }).catch(err => {});
                }else {
                }
            },

            validatesInputLength(){
                return this.gender && this.firstTime &&
                    this.email.length > 0 && this.mobile.length >= 10 &&
                    this.email === this.email_confirm && this.path && this.first_name.length <= 50 && this.last_name.length <= 50 &&
                    this.email.length <= 50 && this.mobile.length <= 25;
            }
        }
    }
</script>


<style src="./../../../../../public/css/bulma-0.6.1/css/bulma.css"></style>
