require 'spec_helper'
module Codebreaker
  describe Game do
    context "#start" do
      let(:game) { Game.new}
 
      before(:each) do
        game.start
      end
 
      it "saves secret code" do
        expect(game.instance_variable_get(:@secret_code)).not_to be_empty
      end
 
      it "saves 4 numbers secret code" do
        expect(game.instance_variable_get(:@secret_code)).to have(4).items
      end
 
      it "saves secret code with numbers from 1 to 6" do
        expect(game.instance_variable_get(:@secret_code)).to match(/[1-6]+/)
      end

    end

    context "#game_progress" do
      let(:game) { Game.new}
 
      before(:each) do
        game.start
	
      end
	it "right number entered" do
	 game.instance_variable_set(:@num, game.instance_variable_get(:@secret_code))
	  game.game_progress
	 expect(game.instance_variable_get(:@msg)).to eq("Congratulations!")
	end
	it "wrong number of args" do
	  wrong = game.instance_variable_get(:@secret_code) + "2"
	  game.instance_variable_set(:@num, wrong)
	  game.game_progress
	 expect(game.instance_variable_get(:@msg)).to eq("Wrong number of arguments \nTry again")
	end
	it "wrong number" do
		number = ""		
		loop do
		number = "#{rand(1..6)}"+"#{rand(1..6)}"+"#{rand(1..6)}"+"#{rand(1..6)}"
		break if number != :@secret_code	
		end
	  game.instance_variable_set(:@num, number)
	  game.game_progress
	 expect(game.instance_variable_get(:@msg)).to eq("Game over")
	end

	it "points system works" do
 	  game.instance_variable_set(:@num, game.instance_variable_get(:@secret_code))
	  game.game_progress
	 expect(game.instance_variable_get(:@pts)).not_to eq(45)
	end
	it "0 points when lose" do
 	 number = ""		
		loop do
		number = "#{rand(1..6)}"+"#{rand(1..6)}"+"#{rand(1..6)}"+"#{rand(1..6)}"
		break if number != :@secret_code	
		end
	  game.instance_variable_set(:@num, number)
	  game.game_progress
	 expect(game.instance_variable_get(:@pts)).to eq(0)
	end

	it "hint works" do
 	  game.instance_variable_set(:@num, "hint")
	  game.game_progress
	 expect(game.instance_variable_get(:@hint)).not_to eq("")
	end

    end

   

  end
end
