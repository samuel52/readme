# Paystackapi
Viola!, welcome to Paystack gem for Ruby API application, this gem is meant to be used by absolute beginners to proffesional ruby and non-ruby developers.. The gem was built out of love for Paystack!. If there's a need to contribute, please do.

### Installation

Simply add this line to your application's Gemfile:

```ruby
gem 'paystackapi'
```

And then execute:

$ bundle

Or install it yourself as:

$ gem install paystackapi

### Usage

require the gem in your controller file where needed.

```ruby
require 'paystackapi'
require 'dotenv/load'
```

###  Transactions

###### Verify Payment

```ruby

def validate_payment
	paystack_ref = params[:reference_code] # collect the payment ref after initializing payment from the frontend
	verify = Paystackapi::PaystackTransactions.verify(paystack_ref)# vola! thats all
end
```
###### Other Transaction Classes

```ruby
 Paystackapi::PaystackTransactions.list # list all transactions
 Paystackapi::PaystackTransactions.totals # show transaction totals
 Paystackapi::PaystackTransactions.list_single(arg) # list single transaction
 Paystackapi::PaystackTransactions.charge(arg) # charge authorization from card
```
### Customers

```ruby
def customers
	customerEmail =  params[:customer_email]
	customer = Paystackapi::PaystackCustomers.create(customerEmail)
end
```
###### Other Customer Classes

```ruby
 Paystackapi::PaystackCustomers.list
 Paystackapi::PaystackCustomers.list_single(arg)
```
### Plans

```ruby
def plans
  createPlan = {
	CustomerName = params[:name]
	interval = params[:interval]
	amount = params[:amount]
  }
  customer = Paystackapi::PaystackPlans.create(createPlan)
end
```
###### Other Plans Classes

```ruby
 Paystackapi::PaystackPlans.list
 Paystackapi::PaystackPlans.list_single(arg)
 Paystackapi::PaystackPlans.update(arg)
 ```
###### Paystack Subscription
```ruby
def subscription
  createSub = {
	CustomerToken = "CUS_xnxdt6s1zg1f4nx"
	planCode = "PLN_gx2wn530m0i3w3m"
  }

customer = Paystackapi::PaystackSubscription.create(createSub)
end
```
###### Other Subcription Classes

```ruby
 Paystackapi::PaystackSubscription.list
 Paystackapi::PaystackSubscription.list_single(arg)
 Paystackapi::PaystackSubscription.disable
 Paystackapi::PaystackSubscription.enable
 ```
### Paystack Transfer
```ruby
def transfer
  createTrans = {
   type = "nuban" #use params[:something] to get the parameters from your endpoint
   name = "Raz"
   description = "Razite"
   account_number = "01000000419"
   bank_code = "044"
   currency = "NGN"
  }
  customer = Paystackapi::PaystackTransfer.generate(createTrans)
end
```
###### Other Transfer Classes

```ruby
 Paystackapi::PaystackSubscription.list_reciept
 Paystackapi::PaystackSubscription.update_reciept(arg, arg)
 Paystackapi::PaystackSubscription.initailize(arg)
 Paystackapi::PaystackSubscription.list_transfer
 Paystackapi::PaystackSubscription.finalize(arg)

 ```
### Bank List
```ruby
Paystackapi::PaystackSubscription.list_banks
```


### Development

After checking out the repo, run `bin/setup` to install dependencies. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

### Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/samuel52/paystackapi. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

### License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

### Code of Conduct

Everyone interacting in the Paystackapi project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/paystackapi/blob/master/CODE_OF_CONDUCT.md).

