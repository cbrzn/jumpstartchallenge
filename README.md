# class Encryptor
	def cipher(rotation)
		characters = (' '..'z').to_a
		rotated_characters = characters.rotate(rotation)
		Hash[characters.zip(rotated_characters)]
 end
 	def encrypt_letter(letter,rotation)
 		cipher_for_rotation = cipher(rotation)
 		cipher_for_rotation[letter]
 	end
 	def encrypt(string, rotation)
 		letters = string.split("")
 		results = []
 		letters.collect do |letter|
 		encrypted_letter = encrypt_letter(letter, rotation)
 		results.push(encrypted_letter)
 			end 	
 		results.join	
 	end
	def decrypt(string, rotation)
 		letters = string.split("")
 		results = []
 		letters.collect do |letter|
 		decrypted_letter = encrypt_letter(letter, -rotation)
  		results.push(decrypted_letter)
 			end
 		results.join
	end
	def encrypt_file(filename, rotation)
		File.open(filename, "r")
		message = File.encrypt(rotation)		
		message_encrypted = File.open(filename, "w")
		message_encrypted.write(" ")
		message_encrypted.close
	end
end
